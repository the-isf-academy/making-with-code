---
title: 3.A.2 CSS Style
draft: True

---

# Customizing the CSS Styles
The design of our todo app is really coming along! 

Bootstrap classes cover a lot of ground. **However, sometimes you will also want to customize them beyond the Bootstrap styles.** To do this,
we can add custom CSS to our to override existing Bootstrap styles or create styles from scratch.

## [A] Overiding Bootstrap classes

**Let's change the background color of the tasks on the `dashboard`.**

{{< code-action >}} **First, open the file, `static/starter_app/custom.css`. You can leave it blank for now.** This is where our custom css will live.

*(Note the file is in the `static` directory, not the `template` directory)*

Next, we need to reference this custom style file in our HTML template. In all our previous changes, we've been changing the
`<body>` portion of our HTML. However, to do this, we need to change the `<head>` portion.

{{< code-action >}} **Add a new head block to our `dashboard.html` template:**
```html {linenos=table, hl_lines=["3-8"]}
{% extends "base.html" %}

{% load static %}

{% block head %}
{{ block.super }}
<link rel="stylesheet" type ="text/css" href="{% static 'starter_app/custom.css' %}">
{% endblock %}

{% block content %}
...
```

> Now, any CSS you write in the `custom.css` file you create will be applied to the dashboard page.

If we want to change the background color used for the list of tasks, we will need to override that CSS property for the `list-group-item` class.

{{< code-action >}} **In `custom.css`, add the following CSS class:**
```css {linenos=table, hl_lines=["1-3"]}
.list-group-item {
    background-color: #81BE11;
}
```

> Refresh the page and you'll see that our labels are now a shade of green that matches the background!


## [B] Custom classes and IDs
Overriding existing Bootstrap classes can go a long way, but **sometimes you will need to change the styles of different groups of HTML elements or even specific instances of an element.** In these cases, you can write custom CSS
classes.

**You can apply a custom CSS class just like you applied the bootstrap class: just give it a definition in your CSS file and add the class name to the component's class list.** Let's create a class so that we can identify task items that
have due dates that are close.

{{< code-action >}} **Add a new class in your `custom.css` file:**
```css {linenos=table, hl_lines=["5-7"]}
.badge-info {
    background-color: #81BE11;
}

.due-soon {
    background-color: #FFFF9C;
}
```

{{< code-action >}} **Then, apply the class you just created to a few tasks on the dashboard:**

```html {linenos=table, hl_lines=[19, 47]}
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
    <li class="list-group-item">
      <div class="d-flex w-100 justify-content-between">
        <h5 class="mb-1">Task</h5>
        <p class="due-soon"><strong>Date Due:</strong> Date holder</p>
      </div>
      <p class="badge badge-info"><i>Label</i></p>

      <p>Notes: notes holder</p>
      <a href="{% url 'update-task' pk=1 %}">
        <button type="button" class="btn btn-outline-secondary btn-sm">
          Update
        </button>
      </a>
    </li>
    <li class="list-group-item">
      <div class="d-flex w-100 justify-content-between">
        <h5 class="mb-1">Task 2</h5>
        <p><strong>Date Due:</strong> Date holder</p>
      </div>
      <p class="badge badge-info"><i>Label</i></p>

      <p>Notes: notes holder</p>
      <a href="{% url 'update-task' pk=2 %}">
        <button type="button" class="btn btn-outline-secondary btn-sm">
          Update
        </button>
      </a>
    </li>
    <li class="list-group-item">
      <div class="d-flex w-100 justify-content-between">
        <h5 class="mb-1">Task 3</h5>
        <p class="due-soon"><strong>Date Due:</strong> Date holder</p>
      </div>
      <p class="badge badge-info"><i>Label</i></p>

      <p>Notes: notes holder</p>
      <a href="{% url 'update-task' pk=3 %}">
        <button type="button" class="btn btn-outline-secondary btn-sm">
          Update
        </button>
      </a>
    </li>
  </ul>
</div>

{% endblock %}
```

> This works for groups of elements that you want to apply styles to, **but what if you need to identify a specific
element?**
>
> For example, let's say we want to highlight the single task with the most urgent due date.

Rather than make a class which could be applied to many elements, **we can use an ID selector that serves as the reference for a single, specific element:**

{{< code-action >}} **In your `custom.css` file, add an ID selector:**
```css {linenos=table, hl_lines=["5-7"]}
.badge-info {
    background-color: #81BE11;
}

.due-soon {
    background-color: #FFFF9C;
}

#due-next {
    background-color: #FFBA8C;
}
```

> *Note that class selectors start with a `.` while ID selectors start with `#`.*

{{< code-action >}} **Then, set the ID for the task that is due next:**
```html {linenos=table, hl_lines=[33]}
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
    <li class="list-group-item">
      <div class="d-flex w-100 justify-content-between">
        <h5 class="mb-1">Task</h5>
        <p class="due-soon"><strong>Date Due:</strong> Date holder</p>
      </div>
      <p class="badge badge-info"><i>Label</i></p>

      <p>Notes: notes holder</p>
      <a href="{% url 'update-task' pk=1 %}">
        <button type="button" class="btn btn-outline-secondary btn-sm">
          Update
        </button>
      </a>
    </li>
    <li class="list-group-item">
      <div class="d-flex w-100 justify-content-between">
        <h5 class="mb-1">Task 2</h5>
        <p id="due-next"><strong>Date Due:</strong> Date holder</p>
      </div>
      <p class="badge badge-info"><i>Label</i></p>

      <p>Notes: notes holder</p>
      <a href="{% url 'update-task' pk=2 %}">
        <button type="button" class="btn btn-outline-secondary btn-sm">
          Update
        </button>
      </a>
    </li>
    <li class="list-group-item">
      <div class="d-flex w-100 justify-content-between">
        <h5 class="mb-1">Task 3</h5>
        <p class="due-soon"><strong>Date Due:</strong> Date holder</p>
      </div>
      <p class="badge badge-info"><i>Label</i></p>

      <p>Notes: notes holder</p>
      <a href="{% url 'update-task' pk=3 %}">
        <button type="button" class="btn btn-outline-secondary btn-sm">
          Update
        </button>
      </a>
    </li>
  </ul>
</div>

{% endblock %}
```

## [C] Now you try
There are many more Bootstrap utilities and components to try out, but they all work the same way. Create the
elements and add the classes as shown in the [Bootstrap documentation](https://getbootstrap.com/docs/4.6/components/alerts/),
and you'll be well on your way to designing snazzy and functional web apps in no time.

{{< code-action >}} **Spend the rest of the lesson exploring the boostrap components and add them to other pages of the todo app to make it more functional and visually appealing.**
