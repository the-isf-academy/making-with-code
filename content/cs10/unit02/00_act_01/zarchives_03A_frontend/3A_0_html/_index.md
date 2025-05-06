---
title: 3.A.0 HTML
draft: true
---

# Intro to HTML

As frontend programmers, you'll be getting very familiar with the language for writing web pages: *HTML* or *hyper text markup language*.
HTML is a language, but it's not a programming language like Python. Instead, it's a language used by your web browser to determine how 
to display web content. You've actually already used a language like this every time you've read a page on this website or written your
self-assessment for a project – MarkDown is a language for rendering content too.

On the internet, HTML runs deep. All webpages are just HTML documents sent to your computer and interpreted by your web browser.

## [A] HTML Basics
HTML documents are made up of different nested elements. This just means that some HTML elements can contain other elements (like a box
inside of a box).
<!-- 
### [The Monster (HTML) Mash]

{{< look-action " To help get a sense of this, work through the following slideshow to make monsters HTML style:" >}}
{{< gdocs src="https://docs.google.com/presentation/d/e/2PACX-1vRYznPe1JhFJ6KoHe5RKLG_vlu3Ujr8l9YyDL1IstA9pTd1xR-7dAaASor4qLXBYth7WORVITBap4oH/embed?start=false&loop=false&delayms=5000" >}} -->

### [HTML Everywhere]
Web programmers make web sites just like you made the monsters above (just with different elements. Let's try to figure out what elements websites are
made of.

{{< code-action "Go to any website (even this one) and open the inspector by right clicking on the page and selecting 'Inspect Element'." >}}  This
will open a new panel of your browser to reveal the HTML that makes up the page you're currently viewing.
<!-- 
{{< write-action >}} Make a table of HTML elements that separates them by whether they can contain other elements. Use the table at the end
of the monster slideshow above as an example. -->

{{< look-action "What HTML elements do you notice? Which elements contain other elements?" >}} Once you've tried categorizing the elements you found, check out [this reference guide](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)
to see all of the kinds of elements you can include in webpages.

### [HTML For Django]
That's a lot of elements! While it is useful to eventually understand and be able to use them all, for now we'll let Django handle a lot
of what we do with HTML. For our purposes, the following HTML elements will be most important:

* **`<div>`** - All "blocks" of content on your page should be wrapped in a `<div>` tag.    
    * If elements beside each other are related in any way (i.e.
parts of a form, paragraphs in a block of text, a section of headers and text, etc.) you should put all of that content in a div. Further, you
will probably end up putting your divs inside other divs (i.e. a div containing many other divs that contain different sections of your homepage).
It's important that you use divs frequently because they will be the most useful way to add style to related elements.
* **text elements** - these will make up the bulk of the content of your web pages.
    * headers (i.e. `<h1>`)
    * paragraphs (`<p>`)
* **structural elements** - this helps quickly organize information on your web pages.
    * ordered lists (`<ol>`)
    * unordered lists (`<ul>`)
    * tables (`<table>`)
    * forms (`<form>`)
* **style elements** - these add different kinds of styles to your web content. You can define what the style actually looks like for these
elements, but the idea behind them is the same across the internet.
    * links (`<a>`)
    * strong (usually **bolded**) text (`<strong>`)
    * idiomatic (usually *italicized* text (`<i>`)
    * line break (`<br>`)

## [B] Getting Started on the Todo App
As you work through the basics of frontend web development, you'll be building a basic todo application. As the frontend developer, you'll be designing the HTML templates and
page styles. After you finish this tutorial, you'll have an example app you can use as a model for your own team's web app.

In this lesson, you will make templates for each of the pages that will ultimately be in the todo app.

### [Setup]
{{< code-action "Before we get started, clone the cs10 Webapp frontend repo on GitHub" >}} , then go into the directory and install the missing packages using pip or pip3.

```shell
cd desktop/cs10/unit_02
git clone https://github.com/the-isf-academy/lab-webapps-frontend-YOUR-GITHUB-USERNAME.git
cd cs10_webapp_frontend-YOUR-GITHUB-USERNAME
pip3 install -r requirements.txt
```

After you have installed the requirements, you can migrate your data and start the server by typing the following in Terminal:

```shell
python3 manage.py migrate
python3 manage.py runserver
```

### [App overview]

**The todo app will have 6 main views.** It's up to you to add them in and stylize them.

- `IndexView()` 
- `TaskDashboardView()`
- `TaskFormView()` 
- `EditTaskView()`
- `CreateAccountView()`
- `LoginView()` 

**To add each of these views, you will need to follow the steps you learned in the previous labs about adding pages to a Django app:**

1. Create a view for the page. We will use class-based views for the views in this tutorial.
1. Add the URL for the page that tells Django which view to use for that URL route.
1. Create a template for the view using HTML.

---

## [C] New Task Page

Let's start by walking through how to create the new task page. This page will look like this after we finish:

{{< figure src="images/courses/cs10/unit02/03A_0_newtask.png" width="100%" title="New Task Page" >}}
 

### [Add the view]
{{< code-action >}} **In `starter_app/views.py`, add a view for the new task page by creawting a class.**

```python {linenos=table, hl_lines=[16,17]}
from django.shortcuts import render
from django.http import HttpResponse
from django.views.generic import ListView, FormView, UpdateView, TemplateView
from django.contrib.auth.mixins import LoginRequiredMixin

#models
from .models import Task

from django.contrib.auth import login, authenticate


# Create your views here.
class IndexView(TemplateView):
    template_name = 'starter_app/indexView.html'

class TaskFormView(TemplateView):
    template_name = 'starter_app/taskFormView.html'
```

### [Add the URL route]

Now that we have the view, we need to Django to route requests for this page to to `NewTaskView()`.

{{< code-action >}} **Add the following line of code to the `starter_app/urls.py` file**

```python {linenos=table, hl_lines=[7]}
from django.urls import path

from . import views

urlpatterns = [
    path('', views.IndexView.as_view(), name='index'),
    path('newtask/', views.TaskFormView.as_view(), name='new-task'),
]
```

#### Add the HTML template
Try running your Django server using `python manage.py runserver` and visit the new task page ([http://127.0.0.1:8000/newtask/](http://127.0.0.1:8000/newtask/)).
You should see an error telling you that the template does not exist. This means we're ready for the final step, making the template
for the page!

{{< code-action >}} **Create a new file called `taskFormView.html` in the `starter_app/templates/starter_app/` directory
and add the code for the base template:**

```python {linenos=table, hl_lines=["1-5"]}
{% extends "base.html" %}

{% block content %}

{% endblock %}
```
> **All of you Django templates for views will start like this, so let's see what happening here.**
> 
> **First, we are telling Django to extend the base template.** Django templates are powerful because they can build on
top of each other. Here, we are building on top of a base template that sets up a foundation for some styling and for
page metadata.
>
> **Second, we are creating a content block.**
> Blocks are how Django puts together templates. The content we put between the `{% block content %}`
and the `{% endblock %}` tags in this file will get inserted in the content section of the `base.html` template. We'll see more of this
kind of block-based templating later in the tutorial.

### [Add the content of the page]

This page will have two parts: a header that says "New Task" and a form to collect the details of a new task.

{{< code-action >}} **First, lets add a div and the header:**

```python {linenos=table, hl_lines=["4-7"]}
{% extends "base.html" %}

{% block content %}
<div>
    <h4>New Task</h4>
</div>
{% endblock %}
```

> The div element will contain the form and its title because they are related elements: they make up our idea of
the form.

{{< code-action >}} **Next, add another div for the form and the code to generate the form:**:

```python {linenos=table, hl_lines=["6-17"]}
{% extends "base.html" %}

{% block content %}
<div>
    <h4>New Task</h4>
    <div>
        <form method="post">
            {% csrf_token %}
            <label for="title">Task:</label><br>
            <input type="text" id="title" name="title"><br>
            <br>
            <label for="due-date">Due Date:</label><br>
            <input type="date" id="due-date" name="due-date"><br>
            <br>
            <button type="submit">Save</button>
        </form>
    </div>
</div>
{% endblock %}
```

> You can [read more about the form element here](https://developer.mozilla.org/en-US/docs/Learn/Forms/Your_first_form), 
but the basics of what we're doing are as follows: 
>
> **All of the form components are wrapped in a form element tag (`<form>`).**
This tag includes a `method` attribute that tells your browser to send a POST HTTP request with the data of the form once
the user clicks submit.
>
> Inside the form are three elements:
> * a text `<input>` field (and it's `<label>`) for the task title
> * a date `<input>` field (and it's `<label>`) for the due date
> * a `<button>` to submit the form
>
> These elements are broken up with line break (`<br>`) to visually divide the different parts of the form.


**Congrats! 🎊 You just added a `new task form` to your Django todo app!**

{{< code-action >}} **Check it out at** [http://127.0.0.1:8000/newtask/](http://127.0.0.1:8000/newtask/)

---

## [D] Now You Try

**Now, your task is to make a page for each of the pages we need in the todo app.**

To do this, you will
probably need to look through how to use some new HTML elements. You can refer to [the HTML refernce guide](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)
to help figure out how to use them.

{{< code-action >}} Use the information and screenshots below to create each of the pages.

### [Index Page]
| View Name             	| URL Route            	| Route Name    | Template Name             | Description                                                                                                                                                        	|
|-----------------------	|----------------------	|-------------- |-------------------------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| `IndexView()`         	| /                    	| index         | `indexView.html`          | The first page that user's see when they visit your app. Gives the user the option to log in or register for a new account.                                        	|


{{< figure src="images/courses/cs10/unit02/03A_0_index.png" width="100%" alt-title="Index Page" >}}

*Hint: HTML `<button>` elements don't naturally act as links. To make your buttons link to the
appropriate pages, you will also need to use link elements (`<a>`) for this page.*

*Also, remember that Django has a special tag for linking within a Django site that uses the name associated with the
URL route rather than the full link (consider why this might be a useful feature). Here's an example for linking
to the login page:*
```python
<a href="{% url 'login' %}">
    ...
</a>
```

### [Dashboard Page]
| View Name             	| URL Route            	| Route Name    | Template Name             | Description                                                                                                                                                        	|
|-----------------------	|----------------------	|-------------- |-------------------------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| `TaskDashboardView()` 	| dashboard/           	| dashboard     | `dashboardView.html`      | Shows all the tasks assigned to the user.                                                                                                                          	|

{{< figure src="images/courses/cs10/unit02/03A_0_dashboard.png" width="100%" title="Dashboard Page" >}}

*Hint: The list HTML elements will come in handy on this page.*

### [Edit Task Page]
| View Name             	| URL Route            	| Route Name    | Template Name             | Description                                                                                                                                                        	|
|-----------------------	|----------------------	|-------------- |-------------------------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| `EditTaskView()`      	| updatetask/\<int:pk\>/ 	| update-task   | `updateTaskView.html`     | Shows a form that lets the user update or delete a task.                                                                                                           	|

{{< figure src="images/courses/cs10/unit02/03A_0_edittask.png" width="100%" alt-title="Edit Task Page" >}}

*Hint: This one will be very similar to the new task page!*

### [Create Account View]
| View Name             	| URL Route            	| Route Name    | Template Name             | Description                                                                                                                                                        	|
|-----------------------	|----------------------	|-------------- |-------------------------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| `CreateAccountView()` 	| register/            	| register      | `createAccountView.html`  | Shows a form that collects information about a new user.                                                                                                           	|

{{< figure src="images/courses/cs10/unit02/03A_0_createaccount.png" width="100%" alt-title="Create Account Page" >}}

*Hint: Use the form elements from the task pages to help get started on this one.*

### [Login View]

{{< figure src="images/courses/cs10/unit02/03A_0_login.png" width="100%" alt-title="Login Page" >}}

*No need to do anything for this one! We'll let Django handle it for us.*

*This view is managed by the Django account plugin and you shouldn't have to edit it.* 	