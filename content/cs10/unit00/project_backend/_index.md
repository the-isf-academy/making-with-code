---
Title: "Project: Backend"
draft: true
---

# Networking: Social Computing Project

In this unit there will be 2 mini-projects for you to create a social computing app. In this part of the project, you will create the SQL and Flask backend. 

{{< aside "Reference Documentation" >}}

- [Flask](https://flask.palletsprojects.com/)
- [SQL](https://docs.python.org/3/library/sqlite3.html)

{{< /aside >}}


---

## [0] Project Planning Document

This is a big project, and you will get lost or frustrated if you don't do some planning up front.
Before you start working on your project, you are required to complete the Project Planning Sheet and meet with a teacher.

✏️ **Fill out your project planning sheet.**

✋ **Meet with a teacher to discuss your idea before beginning to code.**

{{< aside "A few ideas to build on from last year's projects:" >}}

- collaborative story telling (each person adds a new word to a collaborative story)
- r/place, but with emojis or symbols 
- collaborative counting game like [this IRL game](https://dramaresource.com/count-to-20/#:~:text=Sit%20or%20stand%20in%20a,start%20again%20from%20the%20beginning.)
- collaborative hangman

{{< /aside >}}

---

## [1] Starter Code

{{< code-action "Add a shortcut command to easily open Github" >}} 
```shell
echo 'alias remote="open \"\$(git remote get-url origin | sed \"s/\.git\$//\")\""' >> ~/.zshrc
```


{{< code-action "Download your repository with starter code for your project." >}} Be sure to change `yourgithubusername` to your actual Github username.

```shell
cd ~/desktop/making_with_code/unit03_networking/
git clone https://github.com/the-isf-academy/project_networking_backend_yourgithubusername.git
cd project_networking_project_networking_backend_yourgithubusername
```

{{< code-action "Enter the poetry shell." >}}
```shell
poetry shell
```

{{< code-action "Install requirements" >}}
```shell
poetry update
```

<!-- {{< code-action "Install Banjo" >}}
```shell
pip3 install django-banjo
``` -->

The `project_networking` repository containing the following:
  - `\app`
    - `models.py` - This is where you will define your model.
    - `views.py` - This is where you will define your routes and endpoints.
  - `settings.py` - This is where you define your `BASE_URL`
  - `database.sqlite` - This is your database file.
  - `README.md` - This is documentation for the backend of your project.

{{< code-action "Start coding your first milestone!" >}} With you project management sheet approved by a teacher and your starter code downloaded, you're ready to start creating.

---

## [2] Criteria


**This project will be assessed on the following criteria:**
- project planning [3]
- iterative development [3]
- model architecture [3]
- endpoint architecture [3]
- documentation [3]

**For each criteria you will be assessed on a score from 0-3. With 8 criteria, there is a total of 24 potential points.** 
- 0 - no evidence of the practice
- 1 - limited evidence of the practice
- 2 - adequate evidence of the practice
- 3 - substantial evidence of the practice

---

### [Success Claims]

Successful computer scientists should be able to make the following claims:
- I can thoughtfully plan a large computer science project.  
    - I can consider the components of my project before coding
    - I can design the API architecture 
- I can develop my project iteratively over time
    - I can track the development of my project by successfully committing to Github at least once per class work day
    - I can track my current progress and next steps using specific commit messages 
    - I can test my code in small chunks
    - I can identify a Minimum Viable Product (MVP) and complete it before adding additional features
- I can independently write model architecture
  - I can independently build a model with necessary features
  - I can write fields with appropriate data types
  - I can write methods to simplify code
  - I can write code with readability in mind
- I can independently write endpoint architecture
  - I can independently write GET and POST requests
  - I can design endpoints with user experience in mind
  - I can return descriptive and accurate JSON
  - I can return helpful error messages
  - I can write code with readability in mind 
- I can write documentation with public use in-mind
  - I can write a README.md that is clear enough for someone with no prior knowledge of my project to understand
  - I can write a README.md that is complete and accurate to my final project


*Keep these success claims in mind when coding your project and assessing yourself.*

---

## [3] Deliverables


{{< deliverables  >}}

- A `Networking Project: Backend Worksheet` - Paper planning document
- A `project_networking_backend` repository containing the following:
  - `\app`
    - `models.py` - This is where you will define your model.
    - `views.py` - This is where you will define your routes and endpoints.
  - `settings.py` - This is where you define your `BASE_URL`
  - `database.sqlite` - This is your database file.
  - `README.md` - This is documentation for the backend of your project.

---

**🗓️ Timeline**

You have 5 in-class work days. You may find it necessary to work outside of school, however if you are focused in class you can complete the project within the allotted blocks. Our office hours are Wednesdays during CCA in B405. 

| CS10.1 Dates | CS10.2 Dates | Agenda                         |
|--------------|--------------|--------------------------------|
| 14 Oct       | 11 Oct       | Project Intro & MVP |
| 15 Oct       | 17 Oct       | Work Day - MVP                 |
| 18 Oct       | 18 Oct       | Work Day - Peer Review         |
| 23 Oct       | 20 Oct       | Work Day - Documentation       |
| 24 Oct       | 25 Oct       | Due at End of Class            |

---

{{< code-action "Push your work to Github:" >}}
- `git status`
- `git add -A`
    - this adds all changed files to the commit
- `git status`
- `git commit -m "#today I worked on X  #next I will do Y"`
  > be sure to customize this message, do not copy and paste this line
- `git push`
{{< /deliverables >}}
