---
title: "Act III: Developing the App"
type: unit
slug: unit02_web_design
# draft: true
---

# Act III: Developing the App 

You finally get your hands on some code! During Act III you and your partner will delve into the code and see your app start to come to life.


## [0] Starter Code

In this lab, you will be working in groups, storing your shared code in your group's repository.


{{< code-action "Clone your repository with starter code for your project." >}}

```shell
cd ~/desktop/making_with_code/unit05_webapps/
git clone https://github.com/the-isf-academy/project_webapp_flask_GROUPNAME
cd project_webapp_flask_GROUPNAME
```
> replace `GROUPNAME` with your group name
| Group members | Group name |
| --- | --- |
| Ryan & Camilla | swipetune |
| Xandra & Mila | 919 |
| Harry & Ben | harry_ben |
| Ethan & Max | sports |
| Hin Yeung & Justin | McNiche |
| Kabir & Trevor | specialz |
| Hin & Donny | fishfisher |
| Alex & Andy | nba3k |
| Toby & Elliott | phonk |
| Mia & Samuel | pompeii |
| Rex & Darren | chinese_monsters |


{{< code-action "Enter the poetry shell." >}}
```shell
poetry shell
```

{{< code-action "Install requirements" >}}
```shell
poetry install
```


## [1] Assessment


✅  **This project will be assessed based on your ability to achieve your success claims :**

- **Backend**
    - We can define the SQL table with appropriate fields, data types, and default values
    - We can write abstract SQL helper functions to access and manipulate the database
    - We can write route functions to appropriately handle HTTP Requests and return valid responses
    - We can implement forms for user interaction
- **Frontend** 
    - We can decompose our HTML into template files 
    - We can write a readable, correctly structured site using HTML elements 
    - We can write readable, well abstracted and reusable CSS rules to minimize code duplication
    - We can use effectively use classes and IDs to target specific elements for styling
- **Iterative Development**
    - I can track the development of my project by successfully committing to Github at least once per work session
    - I can track my current progress and next steps by writing specific commit messages 
    - I can work on the MVP in small chunks and complete it by the deadline
    - I can consistently update my `README.md` file with works cited


**Your group will be awarded a score from 0-3. There are 6 working days.** 
- 0 - no evidence of the success claims
- 1 - limited evidence of the success claims
- 2 - satisfactory evidence of the success claims
- 3 - substantial evidence of the success claims


---


## [2] Deliverables

{{< deliverables  "At the end of each day, all of the following should be up to date." >}}

- Your Github repository with the most recent app code
- Your `README.md` with your works cited

{{< code-action "Merge your work to Github:" >}}
Follow the steps exactly in order to merge (combine) your work on github. Let a teacher know if you get any error message. 

Student 1:
- `git status`
- `git add -A`
- `git status`
- `git commit -m "your message goes here"`
    - be sure to customize this message, do not copy and paste this line
- `git push`

Student 2:
- `git pull`
- `git status`
- `git add -A`
- `git status`
- `git commit -m "your message goes here"`
    - be sure to customize this message, do not copy and paste this line
    - If you enter a text editor on your terminal, asking for merge message:
        - Press `esc`
        - Type `:wq`
        - Press `enter`
- `git push`

Student 1:
- `git pull`
{{< /deliverables >}}

---

## [3] Flask Reminders 

{{< code-action "To run a local server" >}}  
```shell
python app.py
```

{{< code-action "To open the database in DB Browser" >}}  
```shell
open database.db
```

Helpful Resources
- [Flask Documentation](https://flask.palletsprojects.com/en/stable/)
- [Flask WTF Forms Documentation](https://flask-wtf.readthedocs.io/en/1.2.x/)

---

### To add images from a file

{{< code-action "Add the image to the" >}} **`/static/images` folder.**


{{< code-action "In the HTML template, load the static folder" >}} 

```html
{% load static %}
```


{{< code-action "In the HTML template, reference the static folder in the image tag" >}} 

```html
<img src="{{ url_for('static', filename='images/filename.png') }}">
```


