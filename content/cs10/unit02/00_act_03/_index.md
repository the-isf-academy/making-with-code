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


{{< code-action "Download your repository with starter code for your project." >}}

```shell
cd ~/desktop/making_with_code/unit05_webapps/
git clone https://github.com/the-isf-academy/project_web_apps_group#.git
cd project_web_apps_group#
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

- **Achivement of MVP Success Claims [3]**
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

## [3] Django Reminders 

{{< code-action "To run a local server" >}}  
```shell
python manage.py runserver
```

{{< code-action "To prepare changes the Model fields in the database" >}}  
```shell
python manage.py makemigrations
```

{{< code-action "To apply changes the database" >}}  
```shell
python manage.py migrate
```

{{< code-action "To create a superuser." >}} 
```shell
python manage.py createsuperuser
```

---

### [To add images from a file]

{{< code-action "Add the image to the" >}} **`myapp/static` folder.**


{{< code-action "In the HTML template, load the static folder" >}} 

```html
{% load static %}
```


{{< code-action "In the HTML template, reference the static folder in the image tag" >}} 

```html
<img src="{% static 'filename.png' %}">
```


---


## [3] Backing up your database

In order to back up your database and push it to github, follow these steps:

{{< code-action "Back up your app's database." >}}  
```shell
python manage.py dumpdata > backup.json
```
{{< code-action "Push it to Github" >}}  
```shell
git add backup.json
git status
git commit -m "backing up database"
git push
```



{{< code-action "If you ever want to restore your data from a backup, you can run the following command:" >}}  
```shell
python3 manage.py loaddata backup.json
```

---
