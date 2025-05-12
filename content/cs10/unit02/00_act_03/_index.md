---
title: "Act III: Coding the App"
type: unit
slug: unit02_web_design
draft: true
---

# Act III: Coding the App 

You finally get your hands on some code! During Act III you and your partner will delve into the code and see your app start to come to life.



## [0] Starter Code

In this lab, you will be working in groups, storing your shared code in your group's repository.


our repository with starter code for your project." >}}

```shell
cd ~/desktop/making_with_code/cs10/unit_web_apps/
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

<!-- It contains the following :
- A `project_web_apps` repository containing the following:
  - `\myapp`
    - `models.py` - This is where you will define your model.
    - `views.py` - This is where you will define your routes and endpoints.
  - `database.sqlite` - This is your database file.
  - `README.md` - This is documentation for the backend of your project.
  - `client.py` - This is how the User will interact wiht your server.

{{< code-action "Start coding your first milestone!" >}} With you project management sheet approved by a teacher and your starter code downloaded, you're ready to start creating. -->




## [1] Assessment


✅  **This project will be assessed based on the following success claims:**

- **Iterative Development**
    - I can consistently push my work to Github with descriptive commit messages
    - I can consistently update my `README.md` file with works cited 

- **Coding Implementation**
    - I can stay focused and productive during work sessions
    - I can make a meaningful update to the code in my group's repository each class

- **Problem Solving and Collaboration**
    - I can collaborate well with my partner
    - I can participate in problem solving in an effective manner
    - I can keep the Miro board updated with changes we make to our design


**For each work day from now until E-assessments begin, you will be assessed on a score from 0-3. You will receive an individual score, independent from your partner. With 4 assessed work days, there are a total of 12 potential points.** 
- 0 - no evidence of the success claims
- 1 - limited evidence of the success claims
- 2 - adequate evidence of the success claims
- 3 - substantial evidence of the success claims

{{< expand "Scoring Breakdown" >}}

The project is scored out of 7. 

*To calculate your score for the practices & concepts, look at the following bands:*

- 1 = 0
- 2 = 1
- 3 = 2-3
- 4 = 4-6
- 5 = 7-8
- 6 = 9-10
- 7 = 11-12
{{< /expand >}}


---


## [2] Deliverables

{{< deliverables  "At the end of each day, all of the following should be up to date." >}}

- Your Github repository with the most recent app code
- Your README.md with your works cited
- Your Miro board should be up to date with your design

---

**🗓️ Timeline**

**You have 4 in class days to complete the Miro Planning Board and prepare for the Pitch.**

- begins on Wednesday, 12 April  
- due on Thursday, 20 April

{{< /deliverables >}}

## [3] Backing up your database

In order to back up your database and push it to github, follow these steps:

{{< code-action "Go to your repository:" >}}

```shell
cd ~/desktop/making_with_code/cs10/unit_web_apps/project_web_apps_YOURGROUPNAME
```
{{< code-action "Enter the poetry shell:" >}}  
```shell
poetry shell
```
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
{{< deliverables  "You can stop here! Let your teacher know that your code is live, so that she can load the data on your live sit." >}}

{{< /deliverables >}}


{{< code-action "If you ever want to restore your data from a backup, you can run the following command:" >}}  
```shell
python3 manage.py loaddata backup.json
```

---