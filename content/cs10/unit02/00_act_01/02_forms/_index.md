---
title: 2. Forms
---


# Forms

In this lab, you'll explore how to receive and save data on a web app through a form.

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
## [1] Creating a new color with a form

**Now we're going to extend the app to let users create their own colors.** For this we use [wtfforms](https://wtforms.readthedocs.io/en/3.2.x/) and [flask-wtf](https://flask-wtf.readthedocs.io/en/1.2.x/) libraries. 

{{< code-action >}} **Open `forms.py` and add the following class**

```python {linenos=table}
class ColorForm(FlaskForm):
    name = StringField('Color Name',validators=[DataRequired()])
    red = IntegerRangeField('Red Value', validators=[DataRequired(), NumberRange(min=0, max=100)], default=0)
    green = IntegerRangeField('Green Value', validators=[DataRequired(), NumberRange(min=0, max=100)], default=0)
    blue = IntegerRangeField('Blue Value', validators=[DataRequired(), NumberRange(min=0, max=100)],  default=0)

    submit = SubmitField('Submit')
```
> - `ColorForm` sets up a form that defines which fields are necessary and what data type the field should accept. We use `wtfforms` and `flask-wtf` to easily manage things like validators and default values. 

{{< code-action >}} **Open `app.py` and add the following function**

```python {linenos=table}

@app.route("/new", methods=['GET', 'POST'])
def color_new():
    form = ColorForm()

    if request.method == 'POST':
        if form.validate_on_submit():
            data = form.data 
            new_color(data)

            return redirect(url_for('color_all'))

    return render_template('color_form.html', form=form, heading="Add a new color!")
```
> - `color_new()`, creates an empty `NewColorForm` (e.g.
the name isn't filled in and the colors aren't set) and gives it to the
template, which renders a response. The user sees a page with sliders and a
text field to name the color. 
>   - When the user submits the form (this is a `POST`
request because it's making a change; all the previous requests have been `GET`
requests), `color_new()` again receives the request. This time, since it's a
`POST` with form data (name, color values), it creates a `ColorForm`, checks to
make sure the data is valid, and if so, creates a `Color`, saves it to the
database, and then sends a redirect response telling the user to go to
`/colors`. 
> - `heading="Add a new color!"` is helpful so we can use the same form for multiple use cases, while being able to customize the heading text

{{< code-action >}} **Now go to [`/new`](http://127.0.0.1:5000/new) and add a few color.** Then, go to the [`/all`](http://127.0.0.1:5000/all) page to view your newly added color with all the other colors in the database.


💻 **Currently, you are restricted to a specific range of RGB values -Change the form so you can add an integer from 0-255 for each RGB value.** 


{{< checkpoint >}}

**Before moving on, be sure you understand the following. If you do not, please ask a teacher.**

- What is the purpose of the for loop in the `templates/color_form.html` template file?

{{</ checkpoint >}}


## [2] Modifying a color with a Form

We are going to allow users to update the color if they want to tweak it. For this, we can use the exactly same form!


{{< code-action >}} **In `app.py` and add the following function**

```python {linenos=table}
@app.route("/edit/<int:color_id>", methods=['GET', 'POST'])
def color_edit(color_id):
    color = get_one_color(color_id)
   
    form = ColorForm(data=color)

    if request.method == 'POST':
        if form.validate_on_submit():
            data = form.data 
            
            # finish the function


    return render_template('color_form.html', form=form)
```

{{< code-action >}} **Now go to [`/edit/1`](http://127.0.0.1:5000/edit/1), and make edits.** Try changing the `1` to other numbers. Which numbers work and which numbers do not? 

The form loads and the slides work, however when submitting the form nothing happens.

{{< code-action >}} **Finish the function `color_edit()` to:**
- update the color with the form data
- redirect the user to the detail page


💻 **Add a link on the color detail template that directs you to its edit page.** 

{{< figure src="images/courses/cs10/unit02/02_color_form0.png" width="25%" >}}



{{< checkpoint >}}

**Before moving on, be sure you understand the following. If you do not, please ask a teacher.**

- How is the form pre-populated with the color's data?
- When this form submitted via a  `POST` request, it updates an existing color. How is this different than creating a new color?

{{</ checkpoint >}}

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

--- 

## [4] Extension 

A few ideas of features to extend your learning:
- restrict users editing a color to only move the slides within +/- 10 of its current RGB values
- restrict users to only edit the name of a color instead of the RGB values
- style the form using the `styles.css` file [w3schools css form guide](https://www.w3schools.com/css/css_form.asp)