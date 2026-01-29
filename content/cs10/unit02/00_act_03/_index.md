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
git clone https://github.com/the-isf-academy/project_webapp_group_name.git
cd project_web_app_group#
```
> replace `#` with your group number


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

- **Achievement of MVP Success Claims [3]**
    - We are able to develop our web application to achieve our success claims
    - We can provide appropriate examples to demonstrate success 
- **Iterative Development [3]**
    - I can consistently push my work to Github with descriptive commit messages
    - I can work on my MVP in small chunks
    - I can consistently update my `README.md` file with works cited

**Your group will be awarded a score from 0-3. There are 6 working day.** 
- 0 - no evidence of the success claims
- 1 - limited evidence of the success claims
- 2 - adequate evidence of the success claims
- 3 - substantial evidence of the success claims


---


## [2] Deliverables

{{< deliverables  "At the end of each day, all of the following should be up to date." >}}

- Your Github repository with the most recent app code
- Your README.md with your works cited

{{< code-action "Push your work to Github:" >}}
- `git status`
- `git add index.html`
    - you can add all of the changed files with: `git add -A`
- `git status`
- `git commit -m "your message goes here"`
    - be sure to customize this message, do not copy and paste this line
- `git push`
{{< /deliverables >}}

---

## [3] Flask Reminders 

{{< code-action "To run a local server" >}}  
```shell
python app
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


