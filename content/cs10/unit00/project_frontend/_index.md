---
Title: "Project: Frontend"
draft: true
---

# Networking Frontend Project

In this project, you will create the client frontend for your own or a peer's API.



{{< aside "Key Links" >}}

📖 [Student API Information](https://docs.google.com/spreadsheets/d/1bVw-Sm61f6QHvnHsY5xj3GwQlikyYixXYV-XAeZVdTA/edit?usp=sharing)

📖 [CustomTkinter documentation](https://customtkinter.tomschimansky.com/documentation/)


{{< /aside >}}

---

## [0] Project Planning

Before you start working on your project, you will outline your implementation of the API. 

✏️ **Fill out the "Project Networking Backend Planning Document".** 

👋 **Meet with a teacher to discuss your idea before beginning to code**


---

## [1] Starter Code


{{< code-action "Download your repository with starter code for your project." >}} Be sure to change `yourgithubusername` to your actual Github username.

```shell
cd ~/desktop/making_with_code/unit03_networking/
git clone https://github.com/the-isf-academy/project_networking_frontend_yourgithubusername
cd project_networking_frontend_yourgithubusername
```

{{< code-action "Enter the poetry shell." >}}
```shell
poetry shell
```

{{< code-action "Install requirements" >}}
```shell
poetry install
```

📄 **It contains the following:**
- A `project_networking_frontend` repository containing the following:
  - `client.py` - This is where you will manage the HTTP requests and parse the JSON. 
  - `gui_view.py` - This is where you will manage the logic of your app
  - `gui_template.py` - This creates and runs the apps and contains helper methods

{{< code-action "Start coding your MVP (minimum viable product)!" >}}

---

## [2] Criteria


**This project will be assessed on the following criteria:**
- project planning [3]
- iterative development [3]
- client architecture [3]
- GUI architecture [3]

**For each criteria you will be assessed on a score from 0-3** 
- 0 - no evidence of the practice
- 1 - limited evidence of the practice
- 2 - adequate evidence of the practice
- 3 - substantial evidence of the practice

---

### [Success Claims]

Successful computer scientists should be able to make the following claims:
- I can thoughtfully plan a computer science project
    - I can consider how to implement my client
    - I can sketch wireframes to plan my GUI that consider user interaction
    - I can choose appropriate MVP features 
- I can develop my project iteratively over time
    - I can track the development of my project by successfully committing to Github a minimum of each class work day
    - I can write descriptive commit messages that accurately describe the changes made and state next steps
    - I can systematically break down my project into smaller chunks, priortizing the MVP 
- I can create a client with my chosen API
  - I can create a requests interface that makes get/post requests
  - I can appropriately parse the JSON response
  - I can provide relevant error messages
  - I can use descriptive names for methods, parameters, variables, etc.
  - I can write descriptive comments
- I can create a GUI with user interaction in mind
  - I can write an easy to use client with clear instructions and appropriate formatting
  - I can use descriptive names for properties, methods, parameters, variables, etc.
  - I can write descriptive comments


*Keep these success claims in mind when coding your project and assessing yourself.*


---

## [3] Deliverables

{{< deliverables >}}

**🗓️ Timeline:** It is due on 18 December. You have 6 in-class work days. 

You may find it necessary to work outside of school, however if you are focused in class you can complete the project within the allotted blocks. Our office hours are Wednesday during CCA in B405. 


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
