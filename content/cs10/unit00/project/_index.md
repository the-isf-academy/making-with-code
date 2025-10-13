---
Title: "Project"
draft: true
---

# Networking: Social Computing Project

In this unit you will create the backend of a social computing app using SQL and Flask. 

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

{{< code-action "Download your repository with starter code for your project." >}} Be sure to change `yourgithubusername` to your actual Github username.

```shell
cd ~/desktop/making_with_code/unit03_networking/
git clone https://github.com/the-isf-academy/project_networking_yourgithubusername.git
cd project_networking_project_networking_yourgithubusername
```

{{< code-action "Enter the poetry shell." >}}
```shell
poetry shell
```

{{< code-action "Install requirements" >}}
```shell
poetry install
```

The `project_networking` repository containing the following:
  - `db_definition.sql` - This is where you will define your database tables
  - `init_db.py` - This is what you will run to initalize your database.db file
  - `database.db` - This is your database file.
  - `helpers.py` - This is where you will define helper functions to interact with the database and convert a row to JSON
  - `api.py` - This is where you will define your API endpoints 
  
{{< code-action "Start coding your first milestone!" >}} With you project management sheet approved by a teacher and your starter code downloaded, you're ready to start creating.

---

## [2] Criteria


**This project will be assessed on the following criteria:**
- project planning [3]
- iterative development [3]
- Database SQL functions [3]
- API architecture [3]
- documentation [3]

**For each criteria you will be assessed on a score from 0-3. With 8 criteria, there is a total of 24 potential points.** 
- 0 - no evidence of the practice
- 1 - limited evidence of the practice
- 2 - adequate evidence of the practice
- 3 - substantial evidence of the practice

---

### [Success Claims]

Successful computer scientists should be able to make the following claims:
- I can thoughtfully plan a large computer science project prior to coding.  
    - I can consider social interactions in the design of my database and API
    - I can consider the structure of my database table
    - I can design the API architecture with appropirate HTTP methods and payload
    - I can identify an appropriate Minimum Viable Product (MVP)
- I can develop my project iteratively over time
    - I can track the development of my project by successfully committing to Github at least once per work session
    - I can track my current progress and next steps by writing specific commit messages 
    - I can work on my project in small chunks
- I can independently write database architecture
  - I can define the SQL table with appropriate data types and default values
  - I can write abstract helper functions that execute SQL to interact with the database
  - I can write abstract functions to interact with the database 
  - I can write helper functions to format a row as JSON 
- I can independently write API architecture
  - I can write HTTP requests endpoints with appropriate payload(s)
  - I can return descriptive and accurate JSON with appropriate HTTP status codes
  - I can return helpful error messages with appropriate HTTP status codes 
- I can write code with readability in mind 
  - I can use descriptive names for modules, functions, and variables
  - I can write comments to describe functions and complex pieces of the code
  - I can write a `/help` endpoint that is clear enough for someone with no prior knowledge of my project to understand by providing the HTTP method, route name, and description

*Keep these success claims in mind when coding your project and assessing yourself.*

---

## [3] Deliverables


{{< deliverables  >}}

- A `Networking Project: Backend Worksheet` - Paper planning document
- A `project_networking` repository containing the following:
  - `db_definition.sql` - This is where you will define your database tables
  - `init_db.py` - This is what you will run to initalize your database.db file
  - `database.db` - This is your database file.
  - `helpers.py` - This is where you will define helper functions to interact with the database and convert a row to JSON
  - `api.py` - This is where you will define your API endpoints 

---

**🗓️ Timeline**

You have 5 in-class work days. You may find it necessary to work outside of school, however if you are focused in class you can complete the project within the allotted blocks. Our office hours are Wednesdays during CCA in B403. 

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
