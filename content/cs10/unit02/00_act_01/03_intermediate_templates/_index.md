---
title: 3. Intermediate Templates
# draft: true
---

# Intermediate Templates

In this lab, you'll understand how templates can be super helpful puzzle pieces that easily work together. 

---

## [0] Set up

{{< code-action "Let's begin by starting the Colorama app in a Terminal window." >}} 

```shell
cd ~/desktop/making-with-code/unit05_webapps/lab_flask_colorama_yourgithubusername
```

{{< code-action "Enter the poetry shell." >}}
```shell
poetry shell
```

{{< code-action >}} **Open the repository in VSCode:** `code .` 


---
## A. Templates

This is the current structure of our `templates` directory.

```
templates
├── base.html
├── color_all.html
├── color_detail.html
├── color_form.html
├── color_random.html
├── index.html
├── navbar.html
└── swatch.html
```

Templates are super useful for reducing repetitive code and simplifying editing for the styling of your site. If you want to edit the navigation bar, you just edit `navbar.html`. You don't have to go into every page and edit the navigation bar. 

Let's add a navigation to our page to understand how easily the templates work together. 

{{< code-action >}} **Create a new file `templates/navbar.html` with the following content**


```html {linenos=table}
<div class="nav">
    <a href="{{ url_for('index') }}" style="flex-grow: 4">COLORAMA</a>
    <a href="{{ url_for('color_random') }}">Random</a>
</div>
```

{{< code-action >}} **Now go to [`/new`](http://127.0.0.1:5000/new) and add a few color.** Then, go to the [`/all`](http://127.0.0.1:5000/all) page to view your newly added color with all the other colors in the database.

