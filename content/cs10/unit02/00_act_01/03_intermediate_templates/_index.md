---
title: 3. Intermediate Templates
draft: true
---

# Intermediate Templates

In this lab, you'll understand how templates can be super helpful puzzle pieces that easily work together. 

---

## [0] Set up

{{< code-action "Let's begin by starting the Colorama app in a Terminal window." >}} 

```shell
cd ~/desktop/making-with-code/unit05_webapps/lab_flask_colorama_yourgithubusername
```

{{< code-action "Open the directory in VSCode before starting the app." >}}

```shell
code .
```

{{< code-action "Enter the Poetry Shell and start the app" >}}

```shell
poetry shell
python app.py
```


---

## [1] Navigation Bar

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

{{< code-action >}} **Create a new file `templates/navbar.html`. Reference the below structure for creating your navigation bar.**


```html {linenos=table}
<div class="nav">
    <a href="{{ url_for('index') }}" id="nav-title">SITE TITLE</a>
    <a href="{{ url_for('function_name') }}">Page 1</a>
</div>
```

{{< code-action >}}  **Let's add the navigation bar to every page, by including our new template in the `template/base.html`.** Copy & Paste this line into the `<body>`.

```html {linenos=table}
{% include "navbar.html" %}
```

{{< code-action >}}  **Now explore all of the pages on your site. You should now have a nicely formatted navigation bar!** 

However, it may not be styled as you expect. 

{{< code-action >}}  **Delve into the `static/css/style.css` file to customize your navigation bar**

{{< figure src="images/courses/cs10/unit02/03_templates0.png" width="75%" >}}

---

## [2] Customize the Design 


{{< code-action >}}  **Continue to delve into the `static/css/style.css` file to design of the site!** A few ideas:
- change look of the swatch to look like [Pantone Color Swatches](https://www.pantone.com/media/wysiwyg/blog/jane-boddy/pantone-jane-boddy-neutrals-now-fashion-home-interiors.jpg?auto=webp&format=pjpg&quality=85)
- customize the layout of the all page 
- style the form - [w3schools css form guide](https://www.w3schools.com/css/css_form.asp)



---

## [3] Deliverables

{{< deliverables "Once you've successfully completed the lab:" >}}  


<!-- ☑️  **Fill out [this Google form](https://forms.gle/Xhyi9nk9E3GxJqmx6)** -->

{{< code-action "Push your code to Github." >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}