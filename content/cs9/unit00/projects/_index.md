---
Title: Project
# draft: true
---

# Animation Project

In this project you will make an animated drawing (or a GIF!) using Python's turtle library.

It's up to you to make a drawing you actually care about making. Your teachers will help you choose a project that's a good level of challenge.

Here are a few examples from last year to get you started. 

{{< columns >}}

{{< figure src="images/courses/cs9/unit00/00_project_2022_alden.gif" width="75%" title="by Alden" >}}
<--->
{{< figure src="images/courses/cs9/unit00/00_project_2021_edwin.gif" width="75%" title="by Edwin" >}}
{{< /columns >}}




---

## [0] Project Booklet: Planning 

This is a big project, and you will get lost or frustrated if you don't do some planning up front. You are required to fill out the planning section of the Project Booklet and get it approved by a teacher. 


{{< write-action " ✏️ Fill out the Project Overview and Project Design sections of the Booket." >}}

**✋ Once you have completed your planning document, meet with a teacher to talk through your project.**


---

##  [1] Setup

### Starter Code

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

### Superturtle

{{< aside "Animating with Superturtle" >}}  
You will be using superturtle to create your animation. Check out the documetation for examples of how to use it!

[📖 **Superturtle Animation**](https://superturtle.readthedocs.io/en/latest/animation.html) lets you:

- Rotate
- Scale
- Translate
- Interpolate


[📖 **Superturtle Movement**](https://superturtle.readthedocs.io/en/latest/movement.html) lets you:
- Fly
- Update Position
- *...and more...*

Feel free to use **any** of the superturtle modules in your project!

{{< /aside >}}

---

## [2] Criteria



{{< columns >}}

{{< figure src="images/courses/cs9/unit00/00_project_2022_jay.gif" width="75%" title="by Jay" >}}
<--->
{{< figure src="images/courses/cs9/unit00/00_project_2022_brandon.gif" width="75%" title="by Brandon" >}}
{{< /columns >}}

**This project will be assessed on the following criteria:**
- project managment
- iterative development
- readability
- abstraction
- decomposition

**For each criteria you will be assessed on a score from 0-3:**
- 0 - no evidence of the practice
- 1 - limited evidence of the practice
- 2 - adequate evidence of the practice
- 3 - substantial evidence of the practice

*To do well in this project, you should be able to concretely demonstrate that you can successfully do each practice*

---


### Success Claims

Successful computer scientists should be able to make the following claims:
- I can thoughtfully plan and manage a large computer science project.  
    - I can consider the components of my project before coding
    - I can manage my time well and complete the project by the deadline
    - I can update my process journal on an ongoing basis to organize by thoughts for the next work day
- I can develop my project iteratively over time
    - I can track the development of my project by successfully committing to Github a minimum of each class work day
    - I can write descriptive commit messages that accurately describe the changes made
    - I can systematically breakdown my project into smaller chunks  
- I can write code with readability in mind
    - I can write code as readable as possible for another CS student to understand
    - I can use descriptive names for modules, variables, and functions
    - I can write descriptive comments to describe complex pieces of the code
- I can effectively use the principle of abstraction to make my code more efficient and elegant
    - I can write a function with parameters
    - I can manipulate control flow with conditional statements
    - I can use loops to repeat commands
     can write functions with parameters
- I can effectively use the principle of decomposition to make my code more efficient and elegant
    - I can write functions to be used in different scenarios
    - I can write modules for different aspects of my project

*Keep the success claims in mind when coding your project.*

---

## [3] Deliverables

{{< deliverables  "Your submit the following items:" >}}


- `Unit 00 Animation Project Planning Booklet` handed in to your teacher
- `project_animation` repository containing the following files:
    - `project.py` When this program runs, it should draw your project.
    - `settings.py` This is where you settings for your animation should be stored.
    - `README.md` This is documentation for your project
    - At least one additional module (written by you)


**🗓️ Timeline**

You have 6 in-class work days. You may find it necessary to work outside of school, however if you are focused in class you can complete the project within the allotted blocks. Our office hours are Tuesday during CCA in B405. 

| CS9.1 Dates  | CS9.2 Dates  | Agenda                           |
|--------------|--------------|----------------------------------|
| 07 Nov       | 06 Nov       | Project Intro & Planning Booklet |
| 10 Nov       | 08 Nov       | Work Day                         |
| 15 Nov       | 13 Nov       | Work Day                         |
| 16 Nov       | 14 Nov       | Work Day                         |
| 17 Nov       | 16 Nov       | Work Day                         |
| 21 Nov       | 22 Nov       | Due at End of Class              |

 ---

{{< code-action "Push your work to Github:" >}}
- `git status`
- `git add project.py`
    - you can add multiple files by putting a space inbetween each file
    - *e.g. `git add project.py settings.py`*
- `git status`
- `git commit -m "describe your drawing and your process here"`
  > be sure to customize this message, do not copy and paste this line
- `git push`
{{< /deliverables >}}



## [4] Gallery

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

