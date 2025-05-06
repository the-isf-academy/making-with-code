---
title: 3.A.3 Django Templates
draft: True

---

# Intro to Django Template Language
You now have a foundational understanding of the core elements of web development: HTML and CSS. In this lesson, you will build on
that knowledge to learn how to use Django to make your web pages dynamic.

## [A] Users and authentication
So far, the todo app works the same for every person who visits the site. However, to actually make our todo app work, **we need to make the app do different things depending on who is visiting the site**. You want to see your tasks, not someone else's.

This may seem tricky, but it's actually pretty straightforward. **Django can already manage logging in and who is logged-in in the 
current session of the page. All we need to do is determine what content to show based on who is logged-in.**

{{< expand "Learn More: User Sessions" >}}
Managing user sessions is a really interesting and complex task in modern web development. These kinds of web interactions still
occur entirely through HTTP requests, but web browsers do a lot of extra work to store information about logins to send along with
regular HTTP requests.

If you're interested in learning more about user sessions, you can check out [this resource from the Django documentation](https://django-book.readthedocs.io/en/latest/chapter14.html).

{{< /expand >}}

### [Creating a User]

To get started, we need to make some users for our app.

{{< code-action "First, make sure your database is setup. Run the following command in the top-level directory of the lab:" >}} 
```shell
python3 manage.py migrate
```



{{< code-action "Open the Django shell:" >}} We don't have the web interface setup to register users yet, so we'll use the Django shell to do so instead.
```shell
python3 manage.py shell
```


{{< code-action " Then, run the following commands in the shell to create a new user" >}} (*Make sure to replace the `<>` with the relevant info*):
```shell
>>> from django.contrib.auth.models import User
>>> student_user = User.objects.create_user('<USERNAME>', '<EMAIL>', '<PASSWORD>')
```
> *e.g. `student_user = User.objects.create_user('test_student', 'test@student.com', 'student123')`*

{{< code-action "Check to see if this worked by going to the " >}} [login](http://127.0.0.1:8000/accounts/login/) **page.** Try to
log in with the information you used to create the user.

---

### [User access]

Now we have a user, and we can log in to the app! 🎊 

But... Nothing has really changed about the site. 🤦‍♀️  **There's no way to tell if the user is logged in or not** and a visitor can access all the pages of our site regardless of whether they are logged in.

Let's change that.

**Django let's us easily restrict access to pages if a visitor is not logged in. All we have to do is add the `LoginRequiredMixin` to the views
we want to restrict.**

{{< code-action >}} **Add the `LoginRequiredMixin` to the `TaskDashboardView` class in `views.py`:**

```python {linenos=table, hl_lines=[20]}
from django.shortcuts import render
from django.http import HttpResponse
from django.views.generic import ListView, FormView, UpdateView, TemplateView
from django.contrib.auth.mixins import LoginRequiredMixin

#models
from .models import Task
from .forms import TaskForm, CreateAccountForm

from django.contrib.auth import login, authenticate


# Create your views here.
class IndexView(TemplateView):
    template_name = 'starter_app/indexView.html'

class CreateAccountView(TemplateView):
    template_name = 'starter_app/createAccountView.html'

class TaskDashboardView(LoginRequiredMixin, TemplateView):
    template_name = 'starter_app/dashboardView.html'

class TaskFormView(TemplateView):
    template_name = 'starter_app/taskFormView.html'

class EditTaskView(TemplateView):
    template_name = 'starter_app/updateTaskView.html'
```

{{< code-action >}} **Try logging out and visiting the [dashboard](http://127.0.0.1:8000/dashboard/) page and
then logging in and visiting the page.** Notice the difference?

{{< code-action >}} **Add the `LoginRequiredMixin` to all the views you want to restrict access to.**

{{< aside "Multiple Inheritance" >}}
Notice that we are using *multiple inheritance* with the `LoginRequiredMixin`. Our view classes are now extending
two different parents: the `TemplateView` class and the `LoginRequiredMixin`. Thus, our class can take the properties
and methods of both parents.

If you'd like a more in-depth review of multiple inheritance in Python, check out [this resource](https://www.programiz.com/python-programming/multiple-inheritance).

{{< /aside >}}

---

### [Navbar, revisited]

We've now taken care of how visitors can or cannot access different parts of our site based on their login status. However,
it's still a bit hard to tell whether you are logged in or not. Additionally, it's kind of annoying as a user to have so
many buttons on the navbar that don't do anything.

**Let's update our navbar so that it displays differently when the user is logged-in versus when they are not logged-in.**


In Python, doing this would be pretty straightforward. We could simply use a conditional and some code like this:
```python
if user.is_logged_in:
    display_logged_in_navbar()
else:
    display_logged_out_navbar()
```

Unfortunately, with basic HTML this kind of conditonal code is not possible. HTML is not a programming language.

However, **Django includes a special template language that is a hybrid
between HTML and Python that can do just this.** Even better, this langauge is so intuitive that you've actually been writing
in it the whole time! All of the template pages you've written can include special code that tells Django how to
render the pages.

**Let's see how this works by updating our navbar so that is appears differently depending on whether a user is logged-in.**

{{< code-action >}} **Update your navbar code in `templates/starter_app/navbar.html`:**
```html {linenos=table, hl_lines=["2", "18-20"]}
<nav class="navbar navbar-expand-md navbar-dark bg-dark">
    {% if user.is_authenticated %}
        <a class="navbar-brand" href="{% url 'dashboard' %}">Tasks</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target=".collapse">
            <span class="navbar-toggler-icon"></span>
        </button>
        <ul class="navbar-nav flex-grow-1 navbar-collapse collapse">
          <li class="nav-item active">
            <a class="nav-link" href="{% url 'dashboard' %}">Home <span class="sr-only">(current)</span></a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="{% url 'new-task' %}">New Task</a>
          </li>
          <li class="nav-item ml-md-auto">
            <a class="nav-link" href="{% url 'logout' %}">Log Out</a>
          </li>
        </ul>
    {% else %}
        <a class="navbar-brand mx-auto" href="{% url 'index' %}">Task App </a>
    {% endif %}
</nav>
```
> What's happening here should look pretty familiar to you: we're using an `if` statement to tell Django to use some
HTML content if the current `user` object `is_authenticated`. Then, we're using an `else` statement to tell Django
what content to use in any other case (i.e. the user is not authenticated). 
>
> Finally, because of the conventions of
HTML, we need to tell Django where the end of our `if` statement is since the indentation doesn't matter (which would
signal the end of an `if` in Python.

Now, when you visit the todo app you'll see that the navbar has changed! 

{{< code-action "Try logging in. The navbar will go back to normal!" >}} 

---

## [B] Dyanmic templates
This HTML/Python hybrid template language is actually one of the most powerful features of Django. Whereas in a normal
site you would be stuck with static HTML, **Django let's you make your web pages dynamic, transforming a web site into a web
app.**

You can read about the different feature of the Django template language in [the Django documentation](https://docs.djangoproject.com/en/3.1/ref/templates/language/).
For now, let's explore a few key components: loops and variables.

### [Loops]
It's finally time for our todo app to actually show us real todo tasks rather than the placeholder ones we've had in
the template so far. Let's put some tasks in our database so we have something to work with:

{{< code-action "Start up the Django shell" >}}
```shell
python3 manage.py shell
```

{{< code-action "First, we need to get the user that will create the task" >}} (the one we created at the
beginning of the lab):
```shell
>>> from django.contrib.auth.models import User
>>> our_user = User.objects.first()
>>> our_user
<User: USERNAME>
```

{{< code-action " Then, we can create the task and save it in our database" >}} (*Again, don't forget to replace
the information in the `<>`*):
```shell
>>> import datetime
>>> from starter_app.models import Task
>>> task = Task(task_user=our_user, task_assigned_to=our_user.username, title="<TITLE HERE>", label="<LABEL HERE>", notes="<NOTES HERE>", due_date=datetime.date.today())
>>> task.save()
```
> *e.g. `task = Task(task_user=our_user, task_assigned_to=our_user.username, title="Math Assignment", label="homework", notes="ex. 1-3", due_date=datetime.date.today())`*

{{< code-action "Using the shell, create 2 more tasks for the user." >}} 

Now that we have some tasks in our database, **let's set up our dashboard so that it lists all the tasks for the user who is logged in**.

To do this, we need to get all of the tasks from the database that belong to the user and pass them to our template. Fortunately,
Django has a view which is set up to do exactly that: `ListView`.

{{< code-action >}} **Update the `TaskDashboardView` in the `views.py` file so that it extends the `ListView` class:**
```python {linenos=table, hl_lines=[20]}
from django.shortcuts import render
from django.http import HttpResponse
from django.views.generic import ListView, FormView, UpdateView, TemplateView
from django.contrib.auth.mixins import LoginRequiredMixin

#models
from .models import Task
from .forms import TaskForm, CreateAccountForm

from django.contrib.auth import login, authenticate


# Create your views here.
class IndexView(TemplateView):
    template_name = 'starter_app/indexView.html'

class CreateAccountView(TemplateView):
    template_name = 'starter_app/createAccountView.html'

class TaskDashboardView(LoginRequiredMixin, ListView):
    template_name = 'starter_app/dashboardView.html'

class TaskFormView(LoginRequiredMixin,TemplateView):
    template_name = 'starter_app/taskFormView.html'

class EditTaskView(LoginRequiredMixin,TemplateView):
    template_name = 'starter_app/updateTaskView.html'
```

{{< code-action "Next, we need to tell the view what kind of data we want to list:" >}} 
```python {linenos=table, hl_lines=[22]}
from django.shortcuts import render
from django.http import HttpResponse
from django.views.generic import ListView, FormView, UpdateView, TemplateView
from django.contrib.auth.mixins import LoginRequiredMixin

#models
from .models import Task
from .forms import TaskForm, CreateAccountForm

from django.contrib.auth import login, authenticate


# Create your views here.
class IndexView(TemplateView):
    template_name = 'starter_app/indexView.html'

class CreateAccountView(TemplateView):
    template_name = 'starter_app/createAccountView.html'

class TaskDashboardView(LoginRequiredMixin, ListView):
    template_name = 'starter_app/dashboardView.html'
    model = Task

class TaskFormView(LoginRequiredMixin,TemplateView):
    template_name = 'starter_app/taskFormView.html'

class EditTaskView(LoginRequiredMixin,TemplateView):
    template_name = 'starter_app/updateTaskView.html'
```

{{< code-action "Finally, add a class method that filters the data so that we only get the unarchived tasks for the user who is logged in:" >}}

```python {linenos=table, hl_lines=["24-34"]}
from django.shortcuts import render
from django.http import HttpResponse
from django.views.generic import ListView, FormView, UpdateView, TemplateView
from django.contrib.auth.mixins import LoginRequiredMixin

#models
from .models import Task
from .forms import TaskForm, CreateAccountForm

from django.contrib.auth import login, authenticate


# Create your views here.
class IndexView(TemplateView):
    template_name = 'starter_app/indexView.html'

class CreateAccountView(TemplateView):
    template_name = 'starter_app/createAccountView.html'

class TaskDashboardView(LoginRequiredMixin, ListView):
    template_name = 'starter_app/dashboardView.html'
    model = Task

    def get_context_data(self, **kwargs):
        context = super().get_context_data(**kwargs)

        # filter out archieved tasks
        data = self.model.objects.all().filter(archive=False)

        # filter tasks for user
        tasks = data.filter(task_assigned_to=self.request.user.username)
        context['user_tasks'] = tasks.distinct().order_by('-due_date')

        return context

class TaskFormView(LoginRequiredMixin,TemplateView):
    template_name = 'starter_app/taskFormView.html'

class EditTaskView(LoginRequiredMixin,TemplateView):
    template_name = 'starter_app/updateTaskView.html'
```

Now that we have data about our tasks, we can create HTML elements for each of them. The HTML
for each task looks very similar, and we know what to do when we see repetitive code: use a for loop!
The Django template language provides a for loop to repeat HTML code multiple times.

{{< code-action >}} **Insert a for loop in `dashboardView.html` to repeat the task HTML for each task in**
our data:

```html {linenos=table, hl_lines=[15, 30]}
{% extends "base.html" %}
{% load static %}

{% block head %}
{{ block.super }}
<link rel="stylesheet" type ="text/css" href="{% static 'starter_app/custom.css' %}">
{% endblock %}


{% block content %}
<div class="container" style="width: 75%; margin-bottom: 50px">
    <h4>Tasks</h4>

  <ul class="list-group">
    {% for task in user_tasks %}
        <li class="list-group-item">
          <div class="d-flex w-100 justify-content-between">
            <h5>Task</h5>
            <p class="due-soon"><strong>Date Due:</strong> Date holder</p>
          </div>
          <p class="badge badge-info">Label</p>

          <p>Notes: notes holder</p>
          <a href="{% url 'update-task' pk=1 %}">
            <button type="button" class="btn btn-outline-secondary btn-sm">
              Update
            </button>
          </a>
        </li>
    {% endfor %}
  </ul>
</div>

{% endblock %}
```

Now, you should see a task on the dashboard for each of the tasks you created in the shell at the start of this section!

### Variables

The last step for completing our task dashboard is to populate each task on our dashboard with data from our database.
Each time a view gets rendered, Django sets up a *context* object for the requested view. This context will hold whatever
data we tell it to in the associated view class. We set up our context data in the last section to hold a list of tasks called `user_tasks`.
Then, in the dashboard template, we used a for loop to iterate through each task in the list. Just like in Python, this loop set
up a variable for each object in the list. In this case, we called the variable `task` since each element in the list is one task.
Now, we can access properties of the object in the `task` variable just like we access properties of objects in Python: `task.title`.

{{< code-action >}} Update the `dashboardView.html` template so that it uses the title from each task to fill out the header section
of the task list item:
```html {linenos=table, hl_lines=[18]}
{% extends "base.html" %}
{% load static %}

{% block head %}
{{ block.super }}
<link rel="stylesheet" type ="text/css" href="{% static 'starter_app/custom.css' %}">
{% endblock %}


{% block content %}
<div class="container" style="width: 75%; margin-bottom: 50px">
    <h4>Tasks</h4>

  <ul class="list-group">
    {% for task in user_tasks %}
        <li class="list-group-item">
          <div class="d-flex w-100 justify-content-between">
              <h5>{{ task.title }}</h5>
            <p class="due-soon"><strong>Date Due:</strong> Date holder</p>
          </div>
          <p class="badge badge-info">Label</p>

          <p>Notes: notes holder</p>
          <a href="{% url 'update-task' pk=1 %}">
            <button type="button" class="btn btn-outline-secondary btn-sm">
              Update
            </button>
          </a>
        </li>
    {% endfor %}
  </ul>
</div>

{% endblock %}
```

Great! Now we just need to get the other properties from each task to finish filling out the HTML element.To figure out
what these properties are, we need to look into the *model* for the data. *Models* are templates to add structure to the
data used by our web app. The backend engineer is responsible for setting up the model for the data used in our app. Currently,
our web app has a model for Users and for Tasks. 

{{< code-action >}} Find the model for the `Task` object in `models.py` and use the properties to finish adding task-specific
details to the `dashboardView.html` template.

*Note: all objects also have an ID property (like `task.id`) so that you can uniquely identify each data object. This will
come in handy to make sure that the update button in the task list item links to the correct place.*

## [C] Challenge: Due Next
As a challenge, let's try to apply the style for the task which is due next that we created in the last lab. Remember that you can 
add this style by setting the ID of the element to `due-next` like this:
```html
<p id="due-next"><strong>Date Due:</strong> {{ task.due_date }}</p>
```

However, you will need to figure out how to apply this style to the single element which
is due next. If there are multiple tasks with the same due date, you can just choose one of the
tasks.

*Hints:*
- Consider how the tasks are presented by the for loop. Which task will be the
one with the nearest due date?
- Look through the [Django template tags and filters](https://docs.djangoproject.com/en/3.1/ref/templates/builtins/) and
you should find some helpful tools.
