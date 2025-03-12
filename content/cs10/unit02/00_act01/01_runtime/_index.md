---
title: 2. Runtime Lifecycle
draft: true
---

# Django Runtime

In our first Django lab, we learned about the request/response lifecycle, how
Django's many different parts work together to serve responses to clients. 
**In this second lab on Django, we will consider a longer lifecycle, how Django
works as a Python program from startup to shutdown.** You will also learn about
different ways of running Django, and we'll go into a bit more detail about
requests and responses. 

{{< code-action "Let's begin by starting the Colorama app in a Terminal window." >}} This lab picks up where [Part I](courses/cs10/unit_02/00_request_response/_index.md) left off.

```shell
cd ~/desktop/making-with-code/cs10/unit_web_apps/lab_colorama_yourgithubusername
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

**Django has some nice built-in tools for database backups, which will provide us
with a chance to practice using some new management commands.**

{{< code-action "Back up your app's database." >}}  
```shell
python manage.py dumpdata > backup.json
```
> Note that the `>` redirects the output of a command into a file.
>
> *Try `dumpdata` without `> backup.json`; you'll see all the data printed to your Terminal window.*




{{< code-action "Now that you have a backup of your database, let's test it, shall we? Delete your app's database." >}} 

```shell 
rm db.sqlite3
```
> *Careful! This is permanent. Your backup should work, but we're only suggesting
this because we assume you won't be heart-broken if you lose the colors you
previously created.*


{{< code-action "Let's see what happened by starting to server." >}}  
```shell
python manage.py runserver
```
> [The homepage](http://localhost:8000) still works
because its view doesn't access the database. But the [color list
page](http://localhost:8000/colors) crashes. 


{{< code-action "We can apply database migrations to re-initialize the database:" >}}  
```shell
python manage.py migrate
```

> Now you have a fresh clean database. The [color list page](http://localhost:8000/colors)
should load, but there won't be any colors. 

{{< code-action "Now let's restore data from your backup:" >}}  
```shell
python3 manage.py loaddata backup.json
```

> Double-check the [color list page](http://localhost:8000/colors); all your
colors should be back. 

{{< aside >}}

**🛑 If are you in CS10.1 STOP and update a file.**  

1) Find the file `color_app/fixtures/wikipedia_colors.json`

2) Replace all of its content with this updated version: [wikipedia_colors.json](https://raw.githubusercontent.com/the-isf-academy/lab_colorama/main/color_app/fixtures/wikipedia_colors.json)

{{< /aside >}}


{{< code-action " Now delete your colors again and instead load in" >}}
[all the colors listed on Wikipedia](https://en.wikipedia.org/wiki/Lists_of_colors).
```shell 
rm db.sqlite3
python manage.py migrate
python manage.py loaddata wikipedia_colors.json
```


{{< figure src="images/courses/cs10/unit02/02_colors.png" width="100%" title="Screenshot of app full of colors" >}}

{{< checkpoint >}}

{{< write-action "A.0" >}}  What is the last color when you load in the wikipedia colors?

{{< write-action "A.1" >}} What does it mean to migrate your data?

{{< write-action "A.2" >}} Why is it important to backup your data? 

{{</checkpoint>}}

### [Django Shell]

**Django's shell, like the Banjo shell, is particularly useful for working with models.** The shell is a regular Python shell, but it's loaded in the context of your app and its data.

{{< code-action "Let's explore some of the capabilities of" >}} `Color`.
```shell
python3 manage.py shell
``` 

{{< look-action " First, we'll see some built-in capabilities of any Django model object." >}}

```python
>>> from color_app.models import Color
>>> Color.objects.count()
865
>>> Color.objects.first()
<Color Air Force Blue (Raf) (93, 138, 168)>
>>> Color.objects.last()
<Color Zinnwaldite Brown (44, 22, 8)>
>>> Color.objects.filter(red=255).count()
110
>>> Color.objects.filter(green__gt=200).count() # green > 200
186
>>> Color.objects.filter(name__startswith="R").count()
59
>>> Color.objects.filter(red=255, blue=0).order_by("green")[0:4]
<QuerySet [<Color Red (255, 0, 0)>, <Color Candy Apple Red (255, 8, 0)>, 
<Color Scarlet (255, 36, 0)>, <Color Ferrari Red (255, 40, 0)>]>
```

> **Usually, these kinds of model queries will be used within your app's views.** For
example, if you built a search page, the request might contain values for red,
green, or blue. The view would execute the query and format the result using a
template. 

{{< checkpoint >}}

{{< code-action "These questions require you to use the Django Shell." >}}

{{< write-action "A.3" >}} How many colors start with the letter 'M'?

{{< write-action "A.4" >}}  How many colors have maximum blue and maximum green?

{{< write-action "A.5" >}}  Of the colors with maximum blue and maximum green, which color is lightest? Which color is darkest? 

{{< write-action "A.6" >}} Write the names of all colors containing only blue, sorted by how much blue they contain. 

{{</checkpoint>}}


### [Messing with color]
{{< columns >}}
{{< figure src="images/courses/cs10/unit02/02_rgb.png" width="100%" title="Visualizing RGB color definition" >}}
<--->
{{< figure src="images/courses/cs10/unit02/02_hsv.png" width="100%" title="Visualizing HSV color definition" >}}
{{< /columns >}}



**`Color` also has some custom methods, which we implemented in `color_app/models.py`.**
As it turns out, red/green/blue is not a very convenient color space for finding
related colors. Hue/saturation/value works much better. 

*In the images above, see how you can just rotate the hue to get related colors of the same saturation and value?* The methods below
translate our RGB colors into HSV, adjust the hue, saturation, or value, and
then translate the result back into RGB. Each returns a new `Color`.

{{< look-action " Look at the custom methods of" >}} `Color`.

```python
>>> red = Color(name="red", red=255, green=0, blue=0)
>>> red.hex_code()
'#ff0000'
>>> red.inverted()
<Color red inverted (0, 255, 255)>
>>> red.inverted().hex_code()
'#00ffff'
>>> red_hue = red.adjust_hue(0.5, name="red hue")
>>> red_hue
<Color  (0, 255, 255)>
>>> red_sat = red.adjust_saturation(-0.5, name="red sat")
<Color  (255, 127, 127)>
>>> red_val = red.adjust_value(-0.5, name="red val")
<Color  (127, 0, 0)>
>>> red_hue.save()
>>> red_sat.save()
>>> red_val.save()
```

{{< checkpoint >}}

The next two questions ask about how colors look to you. (Since you saved your reds, 
you can see them down at the end of the [color list page](http://localhost:8000/colors))

{{< write-action "A.7" >}} **How many colors start with the letter 'M'?**
 Adjusting red's hue by 0.5 moved the color halfway around the circle.
*Describe how the resulting color looks to you.*

{{< write-action "A.8" >}} How many colors start with the letter 'M'?
 Describe the perceptual difference between reducing red's saturation by 0.5
  and reducing red's value by 0.5. 

{{</checkpoint>}}

If you're sad that we juet messed up your Wikipedia colors with these reds, you
can just run `red_hue.delete()`, etc. or run `Color.objects.last().delete()` three times.

--- 

## B. Adding color palettes to the app

**Now let's add a new feature to the app: a page for each color which shows a color palette of colors that go nicely together.** This is going to require
extending the app at every level we've studied so far. We'll start at the
"outside" with URL routing, and work our way "in" to the models. 

- **We need to add a URL route** for showing a color. Wo avoid ambiguity, we'll 
  refer to colors by the unique ID each is assigned by the database. These URLs
  will have the form `colors/23`, `colors/155`, etc. 
- **We need a new view** to handle these URLs. 
- **We'll update the color list template** so that each color swatch is a link to
  that color's page.
- **We need a new template** for showing a color.
- **We need to use some settings** to specify how many colors should be shown in the
  palette. 

**Even though we planned this new feature from the outside in, we're going to
implement it from the inside out.** This is a common way to work while designing
web apps. 

{{< code-action "Make the following changes to your files." >}}  You won't
understand it all yet. We highly recommend typing this in yourself rather than
copy-pasting.

{{< aside >}}
The highlighted lines of the code below show the changes you need to make!
{{</ aside >}}

{{< code-action "Add to the bottom of the settings file" >}} : `mysite/settings.py`
```python {linenos=table, hl_lines=["1-3"],linenostart=170}
HUES_TO_SHOW = [-0.16, -0.08, 0, 0.08, 0.16]
SATURATIONS_TO_SHOW = [-0.2, -0.1, 0, 0.1, 0.2]
VALUES_TO_SHOW = [-0.2, -0.1, 0, 0.1, 0.2]
```

{{< code-action "Create a new file for the color detail template:" >}}  `color_app/templates/color_app/color_detail.html`
```html {linenos=table, hl_lines=["1-25"]}
{% extends "base.html" %}
{% load static %}

{% block content %}
  <div class="row">
    <div class="col text-center">
      <h1>{{color.name}}</h1>
      <p>{{color.hex_code}}</p>
      <p>
        <a href="{% url 'color_app:color_list' %}">
          Back to the color list        
        </a>  
      </p>
    </div>      
  </div>
  <h2>Hues</h2>
  <div class="swatches">
    {% for color in hues %}
      <div class="swatch">
        {% include "color_app/swatch.html" %}
      </div>      
    {% endfor %}
  </div>
  <script src="{% static 'color_app/offset_swatches.js' %}"></script>
{% endblock %}
```

{{< code-action "Add links to thr color list template:" >}}  `color_app/templates/color_app/color_list.html`
```python {linenos=table, hl_lines=[2, 6],linenostart=17}
     {% for color in object_list %}
       <a href="{% url 'color_app:color_detail' color.id %}">
       <div class="swatch">
         {% include "color_app/swatch.html" %}
       </div>  
       </a>
     {% endfor %}
```

{{< code-action "Add a view to handle the color detail route:" >}}  `color_app/views.py`:
```python {linenos=table, hl_lines=[5, "18-36"]}
from django.views.generic import DetailView, ListView, CreateView
from django.urls import reverse_lazy
from color_app.models import Color
from color_app.forms import ColorForm
from django.conf import settings

class ColorListView(ListView):
    model = Color
    template_name = "color_app/color_list.html"
    queryset = Color.objects.order_by("name")

class NewColorView(CreateView):
    model = Color
    form_class = ColorForm
    template_name = "color_app/color_form.html"
    success_url = reverse_lazy("color_app:color_list")

class ColorDetailView(DetailView):
    model = Color
    template_name = "color_app/color_detail.html"
      
    def get_context_data(self, *args, **kwargs):
        "Adds properties to the context dict sent to the template" 
        context = super().get_context_data(*args, **kwargs)
        color = self.get_object()
        hues = []
        for adjustment in settings.HUES_TO_SHOW:
            if adjustment == 0:
                hues.append(color)
            else:
                hue = color.adjust_hue(adjustment)
                hue.name = hue.hex_code()
                hues.append(hue)
        context['color'] = color
        context['hues'] = hues
        return context
```

{{< code-action "Add a URL route:" >}} `color_app/urls.py`:
```python {linenos=table, hl_lines=[3, 11]}
from django.urls import path
from color_app import views
from color_app.views import NewColorView, ColorListView, ColorDetailView

app_name = "color_app"
urlpatterns = [
    path('', views.home_view, name="index"),
    path('colors/random', views.random_color_view, name="random_color"),
    path('colors/new', NewColorView.as_view(), name='new_color'),
    path('colors', ColorListView.as_view(), name='color_list'),
    path('colors/<int:pk>', ColorDetailView.as_view(), name='color_detail'),
]
```

**Congratulations! You just added a new feature to the app, and you have a pretty decent color palette generator.**

{{<checkpoint>}}

{{< write-action "B.0" >}} Choose a color palette that you particularly like. What are the hex color values? 

{{< write-action "B.1" >}}  Try changing `HUES_TO_SHOW` in `mysite/settings.py` to display a different number of hues or a different range of adjustment values. You should see the effects on the color detail pages. **What setting of `HUES_TO_SHOW` do you like best?**

{{< write-action "B.2" >}}  We also defined settings for `SATURATIONS_TO_SHOW` and `VALUES_TO_SHOW`, but we're not showing palettes of saturations or values on the color detail
  pages. **Explain the changes you would need to make to show a palette of
  saturations and a palette of values on the color detail page under the 
  palette of hues.**

{{</checkpoint>}}

## C. If you finish early...

Implement the changes you described in B.2 :)


