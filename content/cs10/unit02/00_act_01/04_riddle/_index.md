---
Title: "3. Riddle Game"
draft: true

---

# Riddle Game

In this lab you will use the Riddle Database to create an interactive game.

tasks
- add difficulty to the navbar
- add try again 

---

## [0] Starter Code

{{< code-action "Download your repository with starter code for your project." >}}

```shell
cd ~/desktop/making-with-code/unit05_webapps
git clone https://github.com/the-isf-academy/lab_riddler_django_yourgithubusername
cd lab_riddler_django_yourgithubusername
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

## [1] The Model

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


---


## [2] Session Variables


do we make a worksheet??


{{< checkpoint >}}

✏️💻 **Follow along with the worksheet to understand how this web app is made.** You will be exploring many different files.:

{{</ checkpoint >}}

---

## [3] Flash Messages

{{< code-action >}} **Visit [127.0.0.1:8000/](http://127.0.0.1:8000/) to view the app!** 

<br>




---


## [4] Deliverables 

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

## [5] Extension

### Advanced Index Page

Change the index page to links for difficulty to a dropdown menu. 

For this, you will need to create a form and use the `SelectField` from `flask_wtf`.

allow user to choose number of riddles to guess 

---
<!-- 
### CSS frameworks 

CSS frameworks allow you to easily apply stylels to your web pages. There are many free frameworks. Two of the most common frameworks are Bootstrap and Tailwind. Feel free to test these or explore [other options](https://github.com/troxler/awesome-css-frameworks?tab=readme-ov-file).

- [Boostrap Setup](https://getbootstrap.com/docs/5.3/getting-started/introduction/)
- [Tailwind Setup](https://v3.tailwindcss.com/docs/installation/play-cdn)


 -->
