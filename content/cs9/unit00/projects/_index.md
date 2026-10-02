---
Title: Project
# draft: true
---

# Animation Project

In this project you will make an animated drawing using Python's Turtle library. It must be a self-repeating animation, like a GIF!

It's up to you to make a drawing you actually care about making. Your teachers will help you choose a project that's a good level of challenge.

Here are a few examples from last year to get you started. 

{{< columns >}}

{{< figure src="images/courses/cs9/unit00/00_project_2022_alden.gif" width="75%" title="by Alden" >}}
<--->
{{< figure src="images/courses/cs9/unit00/00_project_2023_claire.gif" width="75%" title="by Claire" >}}
{{< /columns >}}





---

## [0] Project Booklet: Planning 

This is a big project, and you will get lost or frustrated if you don't do some planning up front. You are required to fill out the planning section of the Project Booklet and get it approved by a teacher. 


{{< write-action " ✏️ Fill out the Project Overview and Project Design sections of the Booket." >}}

**✋ Once you have completed your planning document, meet with a teacher to talk through your project.**


---

##  [1] Setup

For this project, your code will live in a git repository. It is your responsibility to regularly commit to your repository.

{{< code-action "Go to your" >}} `unit00_drawing` **folder.**

```shell
cd ~/desktop/making_with_code/unit00_drawing/
```

{{< code-action "Clone your respository with starter code for your project." >}}
```shell
git clone https://github.com/the-isf-academy/project_animation_yourGithubUsername
```
> replace the `yourGithubUsername` with your Github username.
>
> *example:*
>
> *`git clone https://github.com/the-isf-academy/project_animation_emmaqbrown`*



{{< code-action "In the Terminal, type the following command to open the project folder." >}}
```shell
cd project_animation_yourGithubUsername
```

It contains the following files:
- `project.py` When this program runs, it should draw your project.
- `settings.py` This is where you settings for your animation should be stored.
- `README.md` This is documentation for your project for other people who may want to use your project.


{{< code-action "Enter the Poetry Shell." >}} 
```shell
poetry shell
```

{{< code-action "Install the required packages" >}} This project requires SuperTurtle to be installed using poetry. 
```shell
poetry install
```

{{< code-action "Start coding!" >}} With the planning pages of your Project Booklet approved by a teacher and your starter code downloaded, you're ready to start creating.

---


## [2] Criteria


**This project will be assessed on the following criteria:**
- project planning
- iterative development
- readability
- modules
- animation

**For each criteria you will be assessed on a score from 0-3:**
- 0 - no evidence of the criteria
- 1 - limited evidence of the criteria
- 2 - satisfactory evidence of the criteria
- 3 - substantial evidence of the criteria

*To do well in this project, you should be able to concretely demonstrate that you can successfully do each demonstrate each criteria. Substantial evidence requires you to extend beyond the work in the lab.*

---


### Success Claims

Successful computer scientists should be able to make the following claims:
- I can thoughtfully plan a large computer science project.  
    - I can design the details of my modules, functions, and animation prior to coding
- I can develop my project iteratively over time
    - I can track the development of my project by successfully committing to Github at least once per class work session
    - I can track my current progress and next steps by writing specific commit messages 
    - I can work on my project in small chunks
    - I can complete each portion project plan by the corresponding deadline 
- I can write code with readability in mind
    - I can use descriptive names for modules, functions, and variables
    - I can write descriptive comments to describe functions and complex pieces of the code
- I can write modules that effectively use the principles of abstraction and decomposition 
    - I can write functions with parameters that can be used in multiple situations
    - I can use loops to repeat commands, when appropriate
    - I can manipulate control flow with conditional statements, when appropriate 

- I can construct an animation that effectively use the principles of abstraction and decomposition 
    - I can effectively create a self-repeating animation by utilizing `superturtle`
    - I can include customize settings in `setting.py` that customize elements of the animation
    - I can use loops to repeat commands, when appropriate
    - I can manipulate control flow with conditional statements, when appropriate 


---

## [3] Deliverables

{{< deliverables  "Your submit the following items:" >}}


- `Unit 00 Animation Project Planning Booklet` handed in to your teacher
- `project_animation` repository containing the following files:
    - `project.py` When this program runs, it should draw your project.
    - `settings.py` This is where you settings for your animation should be stored.
    - At least one additional module (written by you)

---

**🗓️ Timeline**
- CS9.1 project due on 12 November 
- CS9.2 project due on 09 November

You may find it necessary to work outside of school, however if you are focused in class you should be able to complete the project within the allotted blocks. Our office hours are Wednesday during CCA in B403. 


 ---

{{< code-action "Push your work to Github:" >}}
- `git status`
- `git add -A`
    - you can add multiple files by adding all edited files with `-A`
- `git status`
- `git commit -m "#today what I worked on today #next what I will work on next class"`
  > be sure to customize this message, do not copy and paste this line
- `git push`
- `remote` 
    - check your work is updated on Github
{{< /deliverables >}}



## [4] Gallery


{{< columns >}}

{{< figure src="images/courses/cs9/unit00/00_project_2023_owen.gif" width="75%" title="by Owen" >}}
<--->
{{< figure src="images/courses/cs9/unit00/00_project_2023_kelley.gif" width="75%" title="by Kelley" >}}
{{< /columns >}}

{{< columns >}}

{{< figure src="images/courses/cs9/unit00/00_project_2022_lawrence.gif" width="75%" title="by Lawrence" >}}
<--->
{{< figure src="images/courses/cs9/unit00/00_project_2022_kiki.gif" width="85%" title="by Kiki" >}}

{{< /columns >}}


{{< columns >}}
{{< figure src="images/courses/cs9/unit00/00_project_2021_chris.gif" width="75%" title="by Chris" >}}

<--->
{{< figure src="images/courses/cs9/unit00/00_project_2021_charlotte.gif" width="75%" title="by Charlotte" >}}
{{< /columns >}}


{{< columns >}}

{{< figure src="images/courses/cs9/unit00/00_project_2020_eric.gif" width="75%" title="by Eric" >}}
<--->
{{< figure src="images/courses/cs9/unit00/00_project_2020_austin.gif" width="75%" title="by Austin" >}}
{{< /columns >}}





{{< columns >}}

{{< figure src="images/courses/cs9/unit00/00_project_2023_alex.gif" width="75%" title="by Alex" >}}
<--->
{{< figure src="images/courses/cs9/unit00/00_project_2022_brandon.gif" width="75%" title="by Brandon" >}}
{{< /columns >}}