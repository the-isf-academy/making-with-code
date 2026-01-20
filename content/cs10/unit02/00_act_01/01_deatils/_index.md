---
title: 1. Detail View
# draft: true
---

# Detail View

In this second lab, we will go more in-depth into accessing and manipulating colors from the database.

---

{{< code-action "Let's begin by starting the Colorama app in a Terminal window." >}} This lab picks up where [Part I](courses/cs10/unit_02/00_request_response/_index.md) left off.

```shell
cd ~/desktop/making-with-code/unit05_webapps/lab_colorama_yourgithubusername
```

```shell
poetry shell
python manage.py runserver
```

---

## A. Detail Page


**Now let's add a new feature to the app: a detailed page for each color** This is going to require
extending the app at every level we've studied so far. We'll start at the "outside" with URL routing, and work our way "in" to the models. 
- **We need to add function with a URL** for showing a color. Wo avoid ambiguity, we'll 
  refer to colors by the unique ID each is assigned by the database. These URLs
  will have the form `detail/23`, `detail/155`, etc. Each URL will link to a color swatch.

{{< code-action "Add a view to handle the color detail route:" >}}  `color_app/views.py`:
```python {linenos=table}
@app.route("/detail/<int:color_id>")
def color_detail(color_id):
    color = get_one_color(color_id)

    return render_template(
            'color_detail.html', 
            color = color)
```
> - `/detail/<int:color_id>` - this defines the URL pattern 
> - `def color_detail(color_id)` - this allows you to utilize the integer from the URL pattern
> - *How might you alter this function if you wanted the URL pattern to be `color/name`?*


{{< code-action "Create a new file for the color detail template:" >}}  `/templates/color_detail.html` and copy & paste this code snippet..  

```html {linenos=table}
{% extends "base.html" %}

{% block content %}
  
    <h1>Name: {{color.name}}</h1>

    {% include "swatch.html" %}

{% endblock %}


```

{{< checkpoint >}}

✏️ **What is the purpose of `{% extends "base.html" %}`, `{% block content %}` and `{% endblock %}`?** 


💻✏️ **Add information about the color's RGB value on the detail. How did you do it?** 


💻 **Currently, the only way to see color detail pages is to manually edit the URL. Modify the color all template so you can click on a color swatch and it takes you to its detail page.**

Here is an example of the link pattern. 
```html 
<a href="{{ url_for('color_detail', color_id=1) }}">Click here for Color 1 Detail</a>
```

✏️ **How did you link each swatch?**

{{</ checkpoint >}}

<br>

**🎉 Congratulations! You just added a new feature to the app!**

---

## C. Palette Generator 

Now, let's use the functions in `filters.py` to manipulate the `Color` create a palette generator. Each color detail page will shows a color palette of colors that go nicely together.

{{< figure src="images/courses/cs10/unit02/color_detail0.png" width="50%" >}}



💻 **Let's expand on the `color_detail()` function in `app.py`.** Replace your function with this updated function.

```python {linenos=table}
@app.route("/detail/<int:color_id>")
def color_detail(color_id):
    color = get_one_color(color_id)

    hues = []
    for adjustment in [0.1, 0.2, 0.3]:
        hue = adjust_hue(color, adjustment)
        hues.append(hue)

    return render_template(
            'color_detail.html', 
            color = color, 
            hues = hues,)
```
> - `lines 6-8` - creates new colors based on the requested color using the filter function `adjust_hue()`
> - `line 13` - sends the hues list to the template 


{{< checkpoint >}}

💻 ✏️ **Update your `templates/color_detail.html` to include the hues. How did you do it?** 


{{</ checkpoint >}}



💻  **Utilize the filter `adjust_saturation()` to include an additional color palette on the detail page with saturation adjustments.** Your finished [detail/1](http://127.0.0.1:5000/detail/1) page should look similar to this:

{{< figure src="images/courses/cs10/unit02/color_detail1.png" width="50%" >}}
