---
title: 3.B.1 Django and Models
draft: True

---

# Django and Models

## [A] Setup

{{< code-action >}} Before we get started, please clone the CS10 Webapp backend repo on GitHub, then go into the directory and install the missing packages using pip or pip3.

```shell
cd cs10/unit_02
git clone https://github.com/the-isf-academy/cs10_webapp_backend-YOUR-GITHUB-USERNAME.git
cd cs10_webapp_backend-YOUR-GITHUB-USERNAME
pip3 install -r requirements.txt
```


## [B] Setting up a Model
### [Defining a Model in Django]

A **model** is the single, definitive source of information about your data. It contains the essential fields and behaviors of the data you’re storing. Each model maps to a single database table. We define our models in the `models.py` file.

{{< code-action >}} Open the `models.py` file in the `starter_app` folder and add the following code.

```python
import datetime

from django.db import models
from django.utils import timezone
from django.utils.timezone import now

class Task(models.Model):
    title = models.CharField(max_length=30)
    label = models.CharField(max_length=8)
    notes = models.TextField(editable=True, max_length=200)

    due_date = models.DateField('Date Due', editable=True)
    pub_date = models.DateTimeField('Date Created',default=now, editable=False)
    archive = models.BooleanField(default=False)


    def __str__(self):
        return self.title

    def date_created(self):
        return self.pub_date >= timezone.now() - datetime.timedelta(days=1)

```

Let's look at this code in detail:
- *from django.db import models* enables all of Django's model library code to be used
- There are a couple of django.utils time-based imports
- The *Task* class inherits from Django's Model class. This class definition tells Django that this is a model, and during migration, Django will create the table in the database with the class attributes as database fields
- the class attributes (*title, label, notes, etc*) defines fields (or columns) for the Task table.
- in these class attributes, CharField(max_length=30) defines the type of data the variable will store. CharField(max_length=30) stores a string with a maximum of 30 characters into the database. There are many other field types like IntegerField, DateField, BooleanField, etc. Unlike variables in Python, variables for SQL (the database programming language) are not mutable and cannot change data types.

Django helps map Python to SQL using thees class attributes. For more information, go to the Django reference for Field types is here.
https://docs.djangoproject.com/en/3.1/ref/models/fields/#model-field-types

- There are some parameters like "default" and "editable" in the class attributes. They are used in Django model forms. We will look at these in a later lesson.

- There are two helper class methods *__str__()* and *date_created()* that are used in various places in the app.

Looking at *models.py* , we have a bunch of Django imports and the Task model. We can use this  example code as a template and make other models to use in our system (if needed).


### [Django Migrations]

Before doing anything database related with our model, we need to do a migration. Performing a migration tells Django to (re)build the necessary tables and their fields in our database.

{{< code-action >}} If we've updated any models in *models.py* (like we just did above), we need to make the migrations in the terminal:

```shell
python3 manage.py makemigrations
```

{{< code-action >}} Then, we run the migration:

```shell
python3 manage.py migrate
```

Once we do this, our database will be ready to be used by our app.

{{< code-action >}} Let's try running the server.
```shell
python3 manage.py runserver
```

Now let's see how the model is used in Django.

## [C] Django Models with Django Views

Django can use Models in views to grab data from the database and display the data on the screen.

{{< code-action >}} Let's open `views.py`.

There are a number of view classes in *views.py* that uses the *Task* model. The view will create a Task object which will then get "Task" data from the *Task* table in the database. One such class is *TaskDashboard*.

*TaskDashboard* is a *ListView* which "lists" data records on the screen in a list. The data that is to be shown in the ListView will be pulled from the database using the *Task* model.

Note: This particular view is a ListView and is one of a few Django built-in views that we can use. We won't be looking at views but more info can be found here.
https://docs.djangoproject.com/en/3.1/ref/class-based-views/generic-editing/

*TaskForm* is a *FormView* that will allow the user to submit information about their task. We'll be creating this form in the next step, so we'll need this model to be available.

{{< code-action >}} In `views.py`, **uncomment** line 9 and lines 48-55 so that we can use the *TaskForm* model in the next step.

```python
# from .forms import TaskForm
```

```python
# class TaskForm(LoginRequiredMixin,FormView):
#     template_name = 'starter_app/taskForm.html'
#     form_class = TaskForm
#     success_url = '/dashboard'
#
#     def form_valid(self, form):
#         form.save()
#         return super().form_valid(form)
```

We won't be looking at views in detail. Just know that views use models.

## [D] Django Models with Django Forms

Django can also use Models to automatically create HTML webforms.

{{< code-action >}} Now, let's open `forms.py` and copy the following code into the file.

```python
from django import forms
from .models import Task

class TaskForm(forms.ModelForm):
    class Meta:
        model = Task
        fields = (
            'title',
            'label',
            'notes',
            'due_date',
            )
```
In *forms.py* we import django forms to use them. We also import our Task model to create our Django form.

Our *TaskForm* class inherits ModelForm and uses Task. Django will see this code and automatically builds the form with the fields in *fields* in HTML.  

The *Meta* class is a inner class that has helper functions that changes the behaviour of the model.

This is the basic template for creating forms using models in Django.

{{< code-action >}} Open `urls.py`, we can add the following line of code to use TaskForm as a view.


```python
path('newtask/', views.TaskForm.as_view(), name='new-task'),
```

These lines of code tells Django that the TaskForm class will be used as a view. TaskForm uses the *Task* model to automatically generate a webform and create a *Task* objects for data storage and access. The fields in our Task webform is automatically generated by Django.

Lastly, we need our users to be able to navigate **to** our form, so we will put a link to the form in the navbar at the top of our site.

{{< code-action >}} Open `templates/starter_app/navbar.html`, and add the highlighted lines of code.

```HTML {linenos=table, hl_lines=[9, 10, 11]}
<nav class="navbar navbar-expand-md navbar-dark bg-dark">
  {% if user.is_authenticated %}

    <div class="navbar-collapse collapse w-100 order-1 order-md-0 dual-collapse2">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item active">
            <a class="nav-link" href="{% url 'dashboard' %}">Home <span class="sr-only">(current)</span></a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="{% url 'new-task' %}">New Task</a>
          </li>
        </ul>
    </div>
```

## [E] Putting it Together
### [What We've Made So Far]

{{< code-action >}} Let's try running the server again, and see all of the changes we made!
```shell
python3 manage.py runserver
```

The New Task form and navbar link should look like this:

![New Task Form](/images/courses/cs10/unit02/newtaskform.png)


When a user enters a new task in the New Task page and clicks on "Save", the data will be saved in a Task object and then Django does some *magic* and saves the data into our database.



Let's step through "Adding a new task" use case through the lens of a HTTP request/response:

- A user hits the webpage and the Django server receives HTTP request.
- Django takes the HTTP request and routes the user according to routes defined in *urls.py*. In this case, /newtask/
- Django finds all the parts (Models, Views, Templates, etc) it needs to build the webpage for newtask
- Once Django gathers everything it needs, Django sends the webpage to the user as a HTTP response
- The response is received by our browser and the browser renders the form
- We add a new task and submit the form. That data gets POSTed back to the server
- The server receives the POSTed data and then saves the data into the database in the appropriate table and fields based on the Model

The interaction looks something like this...

![](/images/courses/cs10/unit02/newtask.png)


{{< checkpoint >}}

Use your newly-created form to add at least 3 tasks.

{{</checkpoint >}}

### [Django Shell]

**Now that we have some data in our database, let's see what we can do with it!** We can try out different methods using the python shell.

{{< code-action "Enter the shell" >}}
```shell
python3 manage.py shell
```

{{< code-action " First, we can use the built-in capabilities of any Django model object." >}}

```python
>>> from starter_app.models import Task
>>> Task.objects.count()
3
>>> Task.objects.first()
<Task: Make an NFT>
>>> Task.objects.last()
<Task: Find Eco-Friendly Marketplace>
>>> Task.objects.filter(label='Urgent')
<QuerySet [<Task: Create DAO>]>
>>> Task.objects.filter(archive='False')
<QuerySet [<Task: Make an NFT>, <Task: Create DAO>, <Task: Find Eco-Friendly Marketplace>]>
```

{{< code-action " We can try printing out some of the Task properties" >}}

```python
>>> first_task = Task.objects.first()
>>> print(first_task.title)
Make an NFT
>>> print(first_task.notes)
Contact an artist to make the art and work on creating the smart contract.
>>> print(first_task.due_date)
2022-03-31
```
