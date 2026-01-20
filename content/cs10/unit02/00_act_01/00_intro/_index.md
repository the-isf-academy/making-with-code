---
title: 0. Introduction
---


# Introduction to Web Apps

In this lab, you'll explore a Flask app and make some changes to how it handles
the request/response lifecycle. 


{{< aside "Before we begin, a few reflections" >}}

{{< write-action "At the end of the lab, each student will turn in the answers to the questions in the lab." >}} 

{{< code-action >}} **Do the exploring parts, or you might not understand the questions**. (And we want you to be ready for the rest of the unit.)

 
{{< look-action  >}} **Make sure you actually read the content of this lesson.**

- You will be opening a lot of small files. It takes some practice learning your way around, but you'll get the hang of it.
- Most of the code you're looking at interacts with other code you're not
  seeing. For example, where's the code that actually calls `url_for()` with a
  request? Where's the code that sends the response back to the client? It's all 
  there in the Flask source--there's no magic--but you shouldn't bother reading it. 
- **As you start working
  with larger software packages, you'll need to get used to not
  understanding the whole system.** One of the main goals of computer science is
  to *reduce complexity*--making complicated problems easier to think about. One
  main way we reduce complexity is through *abstraction*, or hiding the parts we
  don't need to think about right now. 
{{</ aside >}}

--- 

{{< code-action >}} **Let's get started by making a `unit_02` folder.**
 
```shell
cd ~/desktop/making-with-code/cs10
mkdir unit05_webapps
cd unit05_webapps
```

{{< code-action "Start by cloning your starter code." >}} Be sure to change `yourgithubusername` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab_flask_colorama_yourgithubusername
cd lab_flask_colorama_yourgithubusername

```

{{< code-action "Enter the poetry shell and install the required packages." >}}
```shell
poetry shell
poetry install
```

{{< code-action >}} **Open the repository in VSCode:** `code .` 


You'll meet some of these files today. For now, **the most important file to know
about is `app.py`.** You'll always run this file when you want Flask to do
anything. 


---
## A. Hello

{{< code-action "Let's start up the app and test it out." >}}  The first command 
prepares the database (more on this later); the second command starts the server
running on port 5000 on your computer. 
```shell
python app.py
```

Now the server is waiting for requests. 

{{< code-action "Head over to your web browser and navigate to:" >}} [http://127.0.0.1:5000](http://127.0.0.1:5000). 

{{< checkpoint >}}
Complete the checkpoints questions on the worksheet as you move through the lab. 

{{< write-action >}} **A.0:** How is it deciding what color is displayed on the page?

{{</ checkpoint >}}

## B. How the parts fit together

Let's see how the parts of the app worked together to show this page. When a
request first arrives, its URL is separated into a host name and a path. In
this case, the host name is `127.0.0.1:5000` and the path is `/`. 

{{< code-action >}} **Open `app.py`.** This where we define the `url paths` and how to handle a request made to that path.

```python{linenos=table}
@app.route("/")
def index():
    color = get_one_color(1)

    name = "Student"

    return render_template(
            'index.html', 
            color=color, 
            name = name)

```
> - `line 1` - defines the url 
> - `line 2` - defines a simple function to receive a `request`, builds a `response`, and returns it
> - `line 3` - calls a helper function to retrieve information from the database
> - `line 7` - returns an HTML file and sends data to the file

---

### [Templates]

***Templates* are pieces of HTML code that can be used to build a webpage.** The
call to `render_template()` on line 21 requests the template `templates/index.html`.
(Every app in the project has a folder called `templates`; when you ask for a
template, Flask searches the folder for a match). 

{{< code-action >}} **Find this template `templates/index.html` and open it.**

```html {linenos=table}
{% extends 'base.html' %}

{% block content %}

  <h1> Hello {{name}}</h1>
  {% include "swatch.html" %}
  <a href="{{ url_for('color_random') }}">How about a random color?</a>.
  
{% endblock %}
```
There's a lot here, so we'll just take a quick tour. This template is made up of
HTML tags like `<h1>...</h1>` and template commands like `{% ... %}` and `{{ ...
}}`. The HTML tags will be read by the client's browser as it presents the webpage; the template
commands tell Flask what to do. 
- `extends` (line 1) means this template extends another template (in this
  case, `base.html`, which you can find in `templates/base.html`.
  Extending another template works by overriding particular *blocks*. Here, we
  are overriding the block called `content` (lines 3-15).
- `{{name}}` (line 5) is a placeholder which will be replaced with the variable called `name` given to the
  template by the function `index()` (`app.py`, lines 24). 
- `include` (line 6) means include another template. Colorama needs to show
  color swatches all over the place, so we have a special template just for the
  color swatch circle. 
- `url_for` (line 9) means look up a url by name (`app`, line 26). Why not
  just type in the url? If you change it later, you might forget to fix it here,
  especially after you have a few dozen templates. And you might want to deploy
  this site to multiple hosts, like `http://127.0.0.1:5000` while you're developing it
  and `colorama.com` when you're ready to go public. 

---

### [Database]
In addition to a template, `home` also uses a the an SQL database table called `colors` (`colors.sql`). 

{{< code-action >}} **The `colors` table is set up like so, check it out by looking opening `colors.sql`**

```sql
CREATE TABLE IF NOT EXISTS colors  (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    red INTEGER NOT NULL,
    green INTEGER NOT NULL,
    blue INTEGER NOT NULL
);
```
> A `Color` has four attributes: `name`, `red`, `green`, and `blue`. (Every pixel
on a computer display has a tiny red, green, and blue light. So every color can
be made by describing how bright each should be.) 

👀 **There are a bunch of helpful functions to access and manipulate the colors table in `helpers.py`**



{{< checkpoint >}}

✏️ **B.0:** When you go to the [home page](http://127.0.0.1:5000), it says "Hello
  stranger" at the top. However, if you look at the template 
  `color_app/templates/index.html`, the word "stranger" does not
  appear. **Explain how the word "stranger" ends up on the page.**
  
  💻 **Then, without changing the template, change the home page so that it says hello to you instead.** Explain what you had to change.

💻  **B.1:** **Change the color swatch on the home page to a different color.** Explain how to do it.

✏️  **B.2:** If you didn't already check it out, go to the [random color page](http://127.0.0.1:5000/random).
  You'll notice that the color swatch changes every time you load the page. **Explain how this works.**

{{</ checkpoint >}}

--- 
## C. Viewing all of the Data

{{< code-action >}} **Open `app.py` and add the following function before `if __name__ == '__main__':`**

```python {linenos=table}
@app.route("/all")
def color_all():
    all_colors = get_all_colors()

    return render_template(
            'color_all.html', 
            all_colors=all_colors)
```
> - `color_all()` accesses all of the colors from the database and then gives them to the template for rendering. 


{{< code-action >}} **Now go to [`/all`](http://127.0.0.1:5000/all), and play around.** You can now add see a list of all the colors. 

{{< code-action >}} **Let's add new Colors directly through the database file.**

0. `open database.db`
0. Use the menu system to create a new row
0. Save the database with (command + s)


{{< checkpoint >}}

**C.0:** There is currently no link from the homepage to the color list, or the
  form to add new colors. You have to enter the URL directly to get to these
  pages, and 99% of users (you no longer included) even know how to enter URLs
  directly. 

- 💻 **Add a link to the home page taking the user to the color list page.**
  *(Hint: There's already a link from the home page to the random color page. Use the same pattern.)*
  
- ✏️ **Explain what you did.** 

**C.1:** There's also no link away from the random color page; you're 
  stuck looping through random colors forever. 
- 💻  **Decide where the random color page should link to add add an appropriate link.** 
- ✏️ **Where did you decide to link to?**

{{</ checkpoint >}}

---

## D. Wrapping up

{{< code-action >}} **Press `Control + C` to kill your server.** 

**In this lesson, you learned the basic structure of a Flask Web app**, by looking at the files and tracing their execution as they handled a basic request and response lifecycle. 

