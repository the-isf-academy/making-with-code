---
Title: "4. Riddle Game"
# draft: true

---

# Riddle Game

In this lab you will use the Riddle Database to create an interactive game.

{{< figure src="images/courses/cs10/unit02/04_riddle0.png" width="50%" >}}

---

## [0] Starter Code

{{< code-action "Download your repository with starter code for your project." >}}

```shell
cd ~/desktop/making-with-code/unit05_webapps
git clone https://github.com/the-isf-academy/lab_flask_riddle_yourgithubusername
cd lab_flask_riddle_yourgithubusername
```

{{< code-action "Install requirements" >}}
```shell
poetry install
```

{{< code-action "Enter the poetry shell." >}}
```shell
poetry shell
```

---

## [1] SQL Table

{{< look-action >}} You can find the `Riddle` table definition in `riddles.sql`

```sql
CREATE TABLE IF NOT EXISTS riddles (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    question TEXT NOT NULL,
    answer TEXT NOT NULL,
    total_guesses INTEGER DEFAULT 0,
    correct_guesses INTEGER DEFAULT 0,
    difficulty TEXT DEFAULT 'easy'
);
```


{{< code-action >}} **Let's start by making the database file by running `python init_db.py`** This file reads in the data from `riddles_data.py`. Feel free to add your own before making the database file.

{{< code-action >}} **Now use the command `ls` and view your `database.db` file** 

{{< aside "Reset Database" >}}

If you want to reset your database, simply delete the database file:

```shell
rm database.db
```

Then, re-run:

```shell
python init_db.py
```

{{< /aside >}}


---


## [2] Complete the Worksheet

{{< code-action "Open the code" >}}
```shell
code .
```

{{< code-action "Start the app and go to:" >}} [127.0.0.1:5000](http://127.0.0.1:5000)
```shell
python app.py
```



{{< checkpoint >}}

✏️💻 **Follow along with the worksheet to understand how this web app is made.** You will learn about:
- [flask wtf fields](https://wtforms.readthedocs.io/en/2.3.x/fields/#basic-fields)
- [session variables](https://flask.palletsprojects.com/en/stable/api/#sessions)
- [flash messages ](https://flask.palletsprojects.com/en/stable/patterns/flashing/)

{{</ checkpoint >}}



---


## [3] Deliverables 

{{< deliverables >}}
{{< code-action "Push your work to Github:" >}}
- `git status`
- `git add -A`
- `git status`
- `git commit -m "your message goes here"`
    - be sure to customize this message, do not copy and paste this line
- `git push`
{{< /deliverables >}}


---

## [3] Extensions

### 404 Page

Currently, if you to a page that doesn't exist, there is an unclear error page with no obvious way to go back to the menu. 

{{< code-action >}} **Add a custom 404 page by adding a new function to `app.py` and a new `404.html` template.** Be sure to include a link in the template to go back to the index page. 

```python
@app.errorhandler(404)
def error_404(error):
    return render_template('404.html'), 404
```

### Custom Favicon

A `Favicon` is the icon that appear on the tab window. 

{{< code-action >}} **Add a favicon**
- add a `.png` file in the `/static` directory 
- link it in the `<head>` of the `base.html` 

```python
<link rel="favicon icon" href="{{ url_for('static', filename='favicon.png') }}">
```

### Other Extension Ideas

- hint system: you can click or hover to reveal the first letter of the answer
- difficulty based scoring: get more points based on difficulty selected
- leaderboard: create a new database that stores users scores and displays them on a new page
- new riddles: allow users to add new riddles to the game
- progress tracking: allow users to see how many questions they have left