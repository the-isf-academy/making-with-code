---
title: 3.A.1 CSS Layout
draft: True
---

# Intro to CSS Layouts
Now that you have the basic map of your site laid out, it's time to learn how to make it more usable by adding some style to your pages.
To add style, we'll use CSS to tell web browsers how to represent the content we've defined semantically in our HTML documents.

## [A] HTML + CSS
**CSS stands for Cascading Style Sheets. CSS styles are predefined ways in which a web browser can represent pieces of content, from bolding them to causing them to fade into view with an animation.**

We can apply multiple styles to a single element and these styles will be interpreted in a predefined way. For example, this allows us to say that all paragraph text in an HTML document should be blue with a font size of 24

```css
.p{
  color: blue;
  font-size: 24px;
}
```

> CSS can be quite specific. Google is your best friend when trying to remember how to customize your styles. 

### [Classes]
CSS classes allow us to write better abstracted code to apply styles to multiple HTML elements.

**To write a CSS class, we choose a name and then choose a particular set of CSS styles that should go with that name.**

For example, the `footnote` class may have styles to make it smaller, italicized, and grey. Then, we can add that class on to any HTML element and those styles will be used:
```html
<p> I think that spiders are really interesting. <p>

<p class="footnote">
   By this I mean that I really hate spiders and
  they scare me a lot. 
</p>
```

The CSS for this `footnote` class may look like:
```css
.footnote{
  color: grey;
  font-style: italic;
  font-size: 8px;
}
```

> *Note that these classes are not the same as Python classes, but they're based on the same idea.*

## [B] CSS Layout
Styling HTML elements can be really difficult and involve a lot of code to make sure that your site uses a consistent style that works well on a variety of screen sizes (this is known as responsive web development). **To help with this, we'll be using a predefined CSS
toolkit that simplifies and standardizes styles across your web app.**

**We will be using CSS classes pre-defined by in
the **[Bootstrap](https://getbootstrap.com/docs/5.1/customize/overview/)** framework.** 

> [This](https://hackerthemes.com/bootstrap-cheatsheet/) is a great resource for Bootstrap tips.

### [Containers]

In Bootstrap, layouts are defined by `container` elements. You can turn any `<div>` into a container simply by adding the `container`
class to the div:

```html
<div class="container">
    <p> I'm a container!</p>
</div>
```

Once a div becomes a container, the width of the div gets limited based on the screen size. This means that content won't overflow on
smaller devices and content won't become really streched on larger devices. Let's see this in action:

{{< code-action >}} **Add the following lines of code to your** `starter_app/dashbaordView.html` file to make the
div contain the tasks in a container with a dark background:

```html {linenos=table, hl_lines=[4,11]}
{% extends "base.html" %}

{% block content %}
<div class="container bg-dark">
    <h4>Tasks</h4>
  <ul>
      <li> <a href="{% url 'update-task' pk=1 %}">Task 1 </a></li>
      <li> <a href="{% url 'update-task' pk=2 %}">Task 2</a></li>
      <li> <a href="{% url 'update-task' pk=3 %}">Task 3</a></li>
  </ul>
</div>

{% endblock %}
```

{{< code-action >}} **Now try changing the size of your browser window to make it bigger and smaller.**

> Notice how the dark background gets smaller as the window gets smaller and bigger as the window gets bigger? That's the power of the Bootstrap container in action!

Containers are very powerful and can be used to make highly customizable webpage layouts using the [Bootstrap
Grid system](https://getbootstrap.com/docs/4.6/layout/grid/). You may want to read more about this later
if you need to make a special layout for one of your pages.

### Flexbox
However, Bootstrap is mostly build on an automative system for intuitively organizing content within containers called the Flexbox layout.

{{< look-action >}} **Watch this brief video describing how the Flexbox layout works:**
{{< youtube "K74l26pE4YA" >}}

Let's use the flexbox layout to add some style the the tasks in our tasklist.

{{< code-action >}} **First, let's change the task elements so that they look more like contained objects than lines of text.** To do this, we'll apply the `list-group` class to our task list element and the 
`list-group-item` to each of the task items in our list:

```html {linenos=table, hl_lines=[6, 7, 10, 13]}
{% extends "base.html" %}

{% block content %}
<div class="container">
    <h4>Tasks</h4> 
  <ul class="list-group">
    <li class="list-group-item">
      <a href="{% url 'update-task' pk=1 %}">Task 1 </a>
    </li>
    <li class="list-group-item">
      <a href="{% url 'update-task' pk=2 %}">Task 2 </a>
    </li>
    <li class="list-group-item">
      <a href="{% url 'update-task' pk=3 %}">Task 3 </a>
    </li>
  </ul>
</div>

{% endblock %}
```

{{< code-action >}} **Next, let's add some more content to our tasks:**

```html {linenos=table, hl_lines=["8-14", "17-23", "26-32"]}
{% extends "base.html" %}

{% block content %}
<div class="container">
    <h4>Tasks</h4> 
  <ul class="list-group">
    <li class="list-group-item">
      <h5 class="mb-1">Task</h5>
      <p><strong>Date Due:</strong> Date holder</p>
      <p><i>Label</i></p>
      <p>Notes: notes holder</p>
      <a href="{% url 'update-task' pk=1 %}">
        Update
      </a>
    </li>
    <li class="list-group-item">
      <h5 class="mb-1">Task</h5>
      <p><strong>Date Due:</strong> Date holder</p>
      <p><i>Label</i></p>
      <p>Notes: notes holder</p>
      <a href="{% url 'update-task' pk=2 %}">
        Update
      </a>
    </li>
    <li class="list-group-item">
      <h5 class="mb-1">Task</h5>
      <p><strong>Date Due:</strong> Date holder</p>
      <p><i>Label</i></p>
      <p>Notes: notes holder</p>
      <a href="{% url 'update-task' pk=3 %}">
        Update
      </a>
    </li>
  </ul>
</div>

{% endblock %}
```

There's a lot of content for each task, and it is a little hard to read since everything is aligned to the left. Let's use a flexbox to rearrange some of the content.

{{< code-action "Make a flexbox for the task name and the due date that spreads the content out across the element:" >}} 

```html {linenos=table, hl_lines=[8, 11, 20, 23, 32, 35]}
{% extends "base.html" %}

{% block content %}
<div class="container">
    <h4>Tasks</h4> 
  <ul class="list-group">
    <li class="list-group-item">
      <div class="d-flex justify-content-between">
        <h5 class="mb-1">Task</h5>
        <p><strong>Date Due:</strong> Date holder</p>
      </div>
      <p><i>Label</i></p>

      <p>Notes: notes holder</p>
      <a href="{% url 'update-task' pk=1 %}">
        Update
      </a>
    </li>
    <li class="list-group-item">
      <div class="d-flex justify-content-between">
        <h5 class="mb-1">Task</h5>
        <p><strong>Date Due:</strong> Date holder</p>
      </div>
      <p><i>Label</i></p>

      <p>Notes: notes holder</p>
      <a href="{% url 'update-task' pk=1 %}">
        Update
      </a>
    </li>
    <li class="list-group-item">
      <div class="d-flex justify-content-between">
        <h5 class="mb-1">Task</h5>
        <p><strong>Date Due:</strong> Date holder</p>
      </div>
      <p><i>Label</i></p>

      <p>Notes: notes holder</p>
      <a href="{% url 'update-task' pk=1 %}">
        Update
      </a>
    </li>
  </ul>
</div>

{% endblock %}
```

These tasks are starting to look a lot better already!

{{< figure src="images/courses/cs10/unit02/03A_1_styled_dashboard.png" width="100%" title="Dashboard with New and Improved Tasks, courtesy of CSS" >}}

There are [many more ways you can use flexboxs to create page layouts](https://getbootstrap.com/docs/4.6/utilities/flex/). 
We recommend trying to make layouts with flexboxes first and then falling back to the Bootstrap grid system if you can't get what you want from the flexbox features.

## [C] Navbar
**Now that you know some layout basics, let's add something a little more complicated: a navbar for your site.** 

This will be essential for directing a user's experience on your app and giving them a consistent feel across the site. To accomplish this, **the navbar will need to be on every page of your site.** 

One way to do this would be to add the code to every page
template you make. However, imagine what would happen if you needed to change a small part of the navbar code: you'd have to go through and change every single page. 🤢

### [Base template]

Django offers a much easier way to do this with **templating**. Remember how all of your templates have extended the `base.html`
template? **If we want to change something about every page on the site, we can just change the base template!**

{{< code-action >}} **Open the base template file `cs10_webapp_base/templates/base.html` and include a new block for the navbar:**

```html {linenos=table, hl_lines=[26]}
{% load static %}


<!doctype html>
<html lang="en">

<head>
{% block head %}
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css" integrity="sha384-MCw98/SFnGE8fJT3GXwEOngsV7Zt27NXFoaoApmYm81iuXoPkFOJwJ8ERdknLPMO" crossorigin="anonymous">
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/js/bootstrap.min.js" integrity="sha384-ChfqqxuZUCnJSK3+MXmPNIyE6ZbWh2IMqE241rYiqJxyMiZ6OW/JmZQ5stwEULTy" crossorigin="anonymous"></script>

    <!-- Custom CSS -->
    <link rel="stylesheet" type ="text/css" href="{% static 'cs10_webapp_base/styles.css' %}">

    <link rel="icon" href="{% static "cs10_webapp_base/favicon.png" %}">
    <title>Starter App</title>

{% endblock %}
</head>
<body>
  {% include 'starter_app/navbar.html' %}
  <div class="container">
    {% block content %}
    {% endblock %}
  </div>
</body>


<!-- Latest compiled and minified JavaScript -->
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
</html>
```

> This will tell Django to look for a file called `navbar.html` in the `templates/starter_app/` directory and insert HTML into the base webpage. 
>
> Now, all we need to do is create HTML for a navbar in the `navbar.html` file.

{{< aside >}}
Did you notice the `{% block content %}` and `{% endblock %}` tags on lines 28 and 29? This is where Django has been inserting the content we've
been writing in the page templates so far!
{{< /aside >}}

### [navbar.html]

{{< code-action >}} **Create a new file `starter_app/navbar.html` and add the following code:**
```html {linenos=table, hl_lines=["1-2"]}
<nav class="navbar navbar-expand-md navbar-dark bg-dark">
</nav>
```

Refresh the page, and you should see a little dark grey bar at the top of your page. That's your navbar! Now,
let's add some content to it.

{{< code-action >}} **First, let's add a home button to the bar (called the "brand"):**

```html {linenos=table, hl_lines=[2]}
<nav class="navbar navbar-expand-md navbar-dark bg-dark">
    <a class="navbar-brand" href="{% url 'dashboard' %}">Tasks</a>
</nav>
```

> Try going to other pages on your app and you'll now see that you can access the dashboard from any page by clicking the home link! Let's add some more functionality to our web app by
adding some more links on the nav bar in a menu.

{{< code-action >}} **Add menu options to explicitly link to the dashboard, the new task page, and the logout page:**
```html {linenos=table, hl_lines=["3-13"]}
<nav class="navbar navbar-expand-md navbar-dark bg-dark">
    <a class="navbar-brand" href="{% url 'dashboard' %}">Tasks</a>
    <ul class="navbar-nav">
      <li class="nav-item active">
        <a class="nav-link" href="{% url 'dashboard' %}">Home <span class="sr-only">(current)</span></a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="{% url 'new-task' %}">New Task</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="{% url 'logout' %}">Log Out</a>
      </li>
    </ul>
</nav>
```

**Notice that we create a nav menu using an unordered list HTML element.** Semantically, this makes sense because menus are just list of options of place you can go on a site. 

Using the semantic list structure will improve our site in two ways. First, it will help people using a screen reader to understand what is happening with this content because the menu options will be presented as a list. Second, it will improve something called SEO (Search Engine Optimization). This means that when a search engine like Google looks through our app, it can rely on the semantic structure of the menu to understand what our
app can do.

### [Return of the flex]

Next, let's add some structure to our navbar. **In many sites, logout is separated from the other menu options to keep users from accidentally logging out.** 

**So, let's try moving the logout button to the right side of our navbar.** To do this, we'll use our handy-dandy flexboxes. Bootstrap nav components are already set as flex boxes, so we can just add the properties we want.

We want to push the last element in our navbar menu all the way to the right of the page. To accomplish
this, we need to change the space around the element rather than the element itself. Every element in HTML
follows the CSS Box Model which includes 3 different ways to change the space around an element:

{{< figure src="images/courses/cs10/unit02/03A_1_box.png" width="100%" title="CSS Box Model" >}}

- *Content* - The content of the box, where text and images appear
- *Padding* - Clears an area around the content. The padding is transparent
- *Border* - A border that goes around the padding and content
- *Margin* - Clears an area outside the border. The margin is transparent

**We can set values for each of these spaces to determine how big they will be.** Further, we can specify different values for the top, right, bottom, and left versions of each of these space *(i.e. margin-top, padding-left)*.

**Since we want to move the logout button all the way to the right, we want to change the left margin around the element to take up as much space as there is available in the navbar.**

Bootstrap flexbox has a cool utility feature that will automatically set the size of the margin depending on how much space there is available.

{{< code-action >}} **First, let's tell the menu to grow as big as possible by adding the `flex-grow` class:**
```html {linenos=table, hl_lines=[3]}
<nav class="navbar navbar-expand-md navbar-dark bg-dark">
        <a class="navbar-brand" href="{% url 'dashboard' %}">Tasks</a>
        <ul class="navbar-nav flex-grow-1">
          <li class="nav-item active">
            <a class="nav-link" href="{% url 'dashboard' %}">Home <span class="sr-only">(current)</span></a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="{% url 'new-task' %}">New Task</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="{% url 'logout' %}">Log Out</a>
          </li>
        </ul>
</nav>
```

{{< code-action >}} **Then, let's tell the logout menu option to automatically add as much left margin as possible by adding the `ml-auto` class:**

```html {linenos=table, hl_lines=[10]}
<nav class="navbar navbar-expand-md navbar-dark bg-dark">
        <a class="navbar-brand" href="{% url 'dashboard' %}">Tasks</a>
        <ul class="navbar-nav flex-grow-1">
          <li class="nav-item active">
            <a class="nav-link" href="{% url 'dashboard' %}">Home <span class="sr-only">(current)</span></a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="{% url 'new-task' %}">New Task</a>
          </li>
          <li class="nav-item ml-auto">
            <a class="nav-link" href="{% url 'logout' %}">Log Out</a>
          </li>
        </ul>
</nav>
```

### [Responsive design]
Our navbar is looking pretty great now! However, what happens if you make the page smaller, maybe the size of a mobile device screen? Things start to look a little funky, right?

**Many (most?) people will probably want to access our webapp from a mobile device, so we need to make sure that our site works well and looks good at all window sizes.** Fortunately, **Bootstrap is built on the principle of
"mobile-first" development**, meaning that all bootstrap components are designed to respond well to different
screen sizes (know as responsive design).

**To make our navbar look and work a little better, we can add CSS so that the nav manu collapses into a [burger menu](https://www.w3schools.com/howto/howto_js_mobile_navbar.asp) once the window gets smaller than a certain size.**

{{< code-action >}} **Let's add the `navbar-collapse` and `collapse` classes to the menu we want to collapse:**

```html {linenos=table, hl_lines=[3]}
<nav class="navbar navbar-expand-md navbar-dark bg-dark">
        <a class="navbar-brand" href="{% url 'dashboard' %}">Tasks</a>
        <ul class="navbar-nav flex-grow-1 navbar-collapse collapse">
          <li class="nav-item active">
            <a class="nav-link" href="{% url 'dashboard' %}">Home <span class="sr-only">(current)</span></a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="{% url 'new-task' %}">New Task</a>
          </li>
          <li class="nav-item ml-auto">
            <a class="nav-link" href="{% url 'logout' %}">Log Out</a>
          </li>
        </ul>
</nav>
```

> Play around with the window size, and you'll see that the menu disappears when the window gets smaller! 
>
> But where did it go?

{{< code-action >}} **Add a button to serve as the menu button:**

```html {linenos=table, hl_lines=["3-5"]}
<nav class="navbar navbar-expand-md navbar-dark bg-dark">
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
          <li class="nav-item ml-auto">
            <a class="nav-link" href="{% url 'logout' %}">Log Out</a>
          </li>
        </ul>
</nav>
```

**One small thing: the logout button is still getting pushed all the way to the right in the menu when the screen is smaller.** This doesn't look so great :/ 

We can fix this by using CSS
to tell the element to only add margin when the window size is larger than a certain *breakpoint*.
If you look at the nav element classes on line 1 above, you'll see that the navbar is set to
expand at the `md` or medium screen size breakpoint because of the class `navbar-expand-md`.

{{< code-action >}} **We can add this same breakpoint to the auto margin class on the logout button by changing the `ml-auto` class to be `ml-md-auto`:**
```html {linenos=table, hl_lines=[13]}
<nav class="navbar navbar-expand-md navbar-dark bg-dark">
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
</nav>
```

**Now, we have a navbar that works well and looks good on all screen sizes!**

{{< figure src="images/courses/cs10/unit02/03A_1_navbar.png" width="100%" title="Dashboard with Bootstrap Navbar" >}}

## [D] Now you try
There are many ways to use Bootstrap layouts like containers and Flexboxes to structure your webpages. You can
explore the [Bootstrap layout documentation](https://getbootstrap.com/docs/4.6/layout/overview/) to learn more,
especially when you realize you need to find a way to create a particular layout.

{{< code-action >}} **For now, use your newly found knowledge of Bootstrap layouts to improve the designs of the other pages of our task app.** 

{{< look-action >}} **Feel free to take a look through the [Bootstrap component library](https://getbootstrap.com/docs/4.6/components/alerts/) to see what kinds of components Bootstrap offers.** 

*Here are some screenshots you can use as guides, but feel free to design them however you like!*

#### Index
{{< figure src="images/courses/cs10/unit02/03A_1_styled_index.png" width="100%" alt-text="Example Styled Index Page" >}}

#### New Task
{{< figure src="images/courses/cs10/unit02/03A_1_styled_new_task.png" width="100%" alt-text="Example Styled New Task Page" >}}

#### Update task
{{< figure src="images/courses/cs10/unit02/03A_1_styled_update_task.png" width="100%" alt-text="Example Styled Update Task Page" >}}

#### Register
{{< figure src="images/courses/cs10/unit02/03A_1_styled_register.png" width="100%" alt-text="Example Styled Account Registration Page" >}}

