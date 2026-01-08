---
title: 1. Detail View
# draft: true
---

# Flask Runtime

In our first Flask lab, we learned about the request/response lifecycle, how
Django's many different parts work together to serve responses to clients. 

**In this second lab on Flask, we will consider a longer lifecycle, how Django
works as a Python program from startup to shutdown.** You will also learn about
different ways of running Django, and we'll go into a bit more detail about
requests and responses. 

{{< code-action "Let's begin by starting the Colorama app in a Terminal window." >}} This lab picks up where [Part I](courses/cs10/unit_02/00_request_response/_index.md) left off.

```shell
cd ~/desktop/making-with-code/unit05_webapps/lab_colorama_yourgithubusername
```

```shell
poetry shell
python manage.py runserver
```

## A. Django management commands

**Every time you run Django, you run `manage.py` with some command.** In Part I, you ran two management commands, `migrate` and `runserver`. You also saw many more, when you ran `python manage.py --list`.  (You can learn more about any command by running `python manage.py runserver --help`.)

**Let's explore a few more commands.**

### [Database management]

**Your app stores its state in a database.** In other words, all its
records--usernames, content, never-ending records of every detail of user 
behavior, financial details (for apps like PayPal), your sexual orientation and who 
you find attractive (for dating apps), whether you have cancer (electronic medical 
records)... your whole online life. 

**If anyone ever got access to your app's database, it could be a disaster for your users.** 
Unfortunately, this happens all the time. (This is a great reason for using a 
framework like Django rather than trying to do it all yourself.)

**Somewhat less disastrous is the situation where an app accidentally loses its own database**, because of a careless programmer mistake (done that!), because a
hard drive fails, or perhaps because you forgot to pay your web hosting bill
(happened to a friend!) Users would find that their account no longer exist, nor
does any of their content. After a restart, the app would behave as if it had
just been launched for the first time. For apps in production (meaning they are available to real-world users), *regular database backups are essential*. That way, even if disaster strikes, at least you can restore the app to the way it was this morning, or last week, or whenever you last backed up the database. 


{{< code-action "What if we were to 'accidentally' delete our database" >}} 

```shell 
rm database.db
```

{{< code-action "Try to visit pages on your site. Is it working?" >}} 

{{< code-action "Create a new database" >}} 

```shell 
python init_db.py
```

## B. Adding color detail page


**Now let's add a new feature to the app: a detailed page for each color** This is going to require
extending the app at every level we've studied so far. We'll start at the "outside" with URL routing, and work our way "in" to the models. 
- **We need to add function with a URL** for showing a color. Wo avoid ambiguity, we'll 
  refer to colors by the unique ID each is assigned by the database. These URLs
  will have the form `colors/23`, `colors/155`, etc. Each URL will link to a color swatch.

{{< code-action "Add a view to handle the color detail route:" >}}  `color_app/views.py`:
```python {linenos=table}
@app.route("/detail/<int:color_id>")
def color_detail(color_id):
    color = get_one_color(color_id)

    return render_template(
            'color_detail.html', 
            color = color)
```
- *What do you think the purpose of the `pk` parameter is?*


{{< code-action "Create a new file for the color detail template:" >}}  `/templates/color_detail.html`.  

```html {linenos=table}
{% extends "base.html" %}

{% block content %}
  
    <h1>{{color.name}}: {{ color|rgb_to_hex }}</h1>

    {% include "swatch.html" %}

{% endblock %}


```
- *How can you display the other fields from the Model (red, green, blue)?*

{{< code-action "Add a link from the color all template page to the color detail:" >}}  `/color_app/color_all.html`. Here is the link pattern. How should you use it? 
```python 
<a href="{{ url_for('color_detail', color_id=color.id) }}">
```



**Congratulations! You just added a new feature to the app!**


## C. Palette Generator 

Now, let's use the methods in the `Color` model to create a palette generator. Each color detail page will shows a color palette of colors that go nicely together.

{{< figure src="images/courses/cs10/unit02/02_colors2.png" width="100%" >}}

You will need to: 
- edit the `color_detail` view 
- edit the `color_app/color_detail.html`
- understand how `adjust_hue()` works 

## D. Deliverables


{{< deliverables "Once you've successfully completed the lab:" >}}  

{{< code-action "Push your code to Github." >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}



