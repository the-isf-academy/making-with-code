---
title: 3.A.4 Themes and Forms
draft: True

---

# Customizing Forms and Theme
You've finally reached the end of this tutorial! To wrap up our work on the frontend side of web apps, let's finish
customizing your web app by updating the forms and the site theme.

## Forms
Since a large part of your web app will be about collecting user data, it's important that you make easy to use data collection
interfaces that get the data your architect will need from the user. Currently, all of the data collection forms on our web app are the same,
static form. However, you will need to customize these form to meet the need of your web app.

Fortunately, Django is setup to easily generate useful forms based on the data models created by the backend architect. All you need
to do is tell Django where to put the form (in the template) and what to do with the data once it's collected (in the view).

### Form Views
Let's start by updating the view for a page which holds a form, the account registration page.

{{< code-action >}} **First, add some code to `starter_app/forms.py`:**
```python {linenos=table, hl_lines=["6-24"]}
from django import forms
from .models import Task
from django.contrib.auth.forms import UserCreationForm
from django.contrib.auth.models import User

class TaskForm(forms.ModelForm):
    class Meta:
        model = Task
        fields = (
            'title',
            'label',
            'notes',
            'due_date',
            'task_assigned_to'
            )

class CreateAccountForm(UserCreationForm):
    class Meta:
        model = User
        fields = (
            'username',
            'password1',
            'password2'
            )
```
This code is creating a class for each form we'll put on our site and defining what fields that form should have. The
backend architect has control over this part of our site because they get to decide what data we need to collect and how
we should collect it.

{{< code-action >}} **In the `views.py` file, update the `CreateAccountView` class so that it extends the `FormView` class:**
```python {linenos=table, hl_lines=[8, "17-30"]}
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

class CreateAccountView(FormView):
    template_name = 'starter_app/createAccountView.html'
    form_class = CreateAccountForm
    success_url = '/dashboard'

    def form_valid(self, form):
        # This method is called when valid form data has been POSTed.
        # It should return an HttpResponse.
        form.save()
        username = form.cleaned_data.get('username')
        raw_password = form.cleaned_data.get('password1')
        user = authenticate(username=username, password=raw_password)
        login(self.request, user)
        return super().form_valid(form)

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

Now, our `CreateAccountView` class will contain a form object (designed by the backend architect and pulled from `forms.py`).
Additionally, the `form_valid()` function tells Django what to do with the data once the form is submitted: create a new user
with the information provided and log the user in.

{{< code-action >}} **Next, add the form object to the template in `createAccountView.html`:**
```python {linenos=table, hl_lines=[2, 12]}
{% extends "base.html" %}
{% load crispy_forms_tags %}


{% block content %}
  <div class="d-flex justify-content-center">
    <div class="card">
        <div class="card-body">
        <h4 class="card-title">Sign up for an account!</h4>
        <form method="post" >
            {% csrf_token %}
            {{ form|crispy }}
            <button type="submit" class="btn btn-dark">Save</button>
        </form>
        </div>
    </div>
  </div>
{% endblock %}
```

That's it! Given the relatively well-structured nature of data collection, Django knows how to create the HTML form
elements to get the data we need!

### Task Creation and Updates
Let's do the same for the task creation and updating forms.

{{< code-action >}} **Update the `TaskFormView` and `EditTaskView` classes in `views.py`:**
```python {linenos=table, hl_lines=["50-78"]}
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

class CreateAccountView(FormView):
    template_name = 'starter_app/createAccountView.html'
    form_class = CreateAccountForm

    success_url = '/dashboard'


    def form_valid(self, form):
        # This method is called when valid form data has been POSTed.
        # It should return an HttpResponse.
        form.save()
        username = form.cleaned_data.get('username')
        raw_password = form.cleaned_data.get('password0')
        user = authenticate(username=username, password=raw_password)
        login(self.request, user)
        return super().form_valid(form)

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

class TaskFormView(LoginRequiredMixin,FormView):
    template_name = 'starter_app/taskFormView.html'
    form_class = TaskForm
    success_url = '/dashboard'


    def form_valid(self, form):
        # This method is called when valid form data has been POSTed.
        # It should return an HttpResponse.

        if form.instance.task_assigned_to == "":
            form.instance.task_assigned_to = self.request.user.username

        form.instance.task_user = self.request.user
        form.save()
        return super().form_valid(form)

class EditTaskView(LoginRequiredMixin,UpdateView):
    model = Task
    template_name = 'starter_app/updateTaskView.html'
    success_url = '/dashboard'

    fields = [
        "title",
        "label",
        "notes",
        "archive",
        "due_date"
    ]
```

Again, we need to tell the views what models the forms should be based off of. However, we only need to tell Django what to
do once the forms are submitted for the `TaskViewForm` class. Django is smart enough to know that the form should update
the database when the form from the update page is submitted.

{{< code-action >}} **Finally, we can update the `taskFormView.html` and `updateTaskFormView.html` templates. Update them the same
way you updated the account registration template above.**

Woohoo! Our webapp is fully functional now! You can create accounts, log in, create new tasks, and update existing tasks all from
the web app!

## Themes
Last but not least, let's update your site's theme so that it matches the aesthetic you want to cultivate for your
webapp. There are many way to update the theme (including by writing all custom CSS classes), but here is one quick
and easy way.

{{< code-action >}} Start by heading to [this Bootstrap theme website](https://bootswatch.com/) and selecting a theme you like.

{{< code-action >}} Once you've selected a theme, download it by clicking on the theme name in the nav bar and selecting `bootstrap.min.css`.

{{< code-action >}} Next, open the base CSS file for your webapp, `cs10_webapp_base/static/cs10_webapp_base/styles.css`.

{{< code-action >}} Copy and paste the contents from the file you downloaded into your `styles.css` file.

Reload your page and your webapp should now be using the color palatte you selected.

---

**Congrats! You've made it to the end of the frontend tutorial! You're now a certified cs10 Designer! 🎖**

Get ready to apply your newfound skills to making your own app.
