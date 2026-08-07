---
title: 10. SuperTurtle
draft: true
---

# SuperTurtle Lab

In this lab we are going to explore different ways you can animate using a package called `SuperTurtle`. This will require us to understand a key computer science concept, decomposition.

---

## [0] What is Decomposition?

Decomposition is the act of breaking down a problem into smaller, more manageable parts. This is an incredibly useful problem solving technique, even outside of computer science.

For example, let's consider the problem of baking a birthday cake. We can break this down into large overarching pieces such as the cake, the icing, and the assembly. Then each of those pieces can be broken down even further until you get to each individual ingredient.
- cake  
  - mixing the batter
    - dry ingredients
    - wet ingredients
  - baking the batter
    - temperture
    - time
  - cooling the cake
- icing
  - mixing the icing
    - flavor
    - color
- assemble the cake
  - frost the cake
  - add sprinkles

When thinking about complex problems there are two ways to approach them: top-down and bottom-up. Some people like to start with top-down thinking; others prefer bottom-up. Usually we need to use both.

- Top down means thinking about the problem as a whole, and how it could be broken up into a few smaller pieces. Then each of those smaller pieces could be broken into even smaller pieces.

- Bottom-up means starting with tiny chunks that are so simple we can already solve them, and using them to build gradually larger pieces, until you've solved the problem.

For example, let's consider baking again.
- Top-down: You need to make a birthday cake, and so you figure out the steps and the ingredients.  
- Bottom-up: You take a look at your all of your baking supplies and ingredients at home, and figure out you can make a birthday cake.

---

## [1] Set Up

{{< code-action "Add a shortcut command to easily open Github" >}} 
```shell
echo 'alias remote="open \"\$(git remote get-url origin | sed \"s/\.git\$//\")\""' >> ~/.zshrc
```

{{< code-action "Go to your" >}} `unit00_drawing` **folder.**

```shell
cd ~/desktop/making_with_code/unit00_drawing/
```

{{< code-action "Clone your repo. This will copy it onto your computer." >}}  
```shell
git clone https://github.com/the-isf-academy/lab_superturtle_yourGithubUsername
```
> Below you'll see that the `git clone` command has a `yourGithubUsername`. 
>
> **You need to replace this with your username**
>
> *e.g. `https://github.com/the-isf-academy/lab_superturtle_emmaqbrown`*




{{< code-action "In the Terminal, type the following command to open the lab folder." >}}
```shell
cd lab_superturtle_yourGithubUsername
```


{{< code-action "Enter the Poetry Shell to start the lab." >}} We will run this command at the start of each lab, but only when we are inside a lab folder.
```shell
poetry shell
```

{{< code-action >}} This lab uses a package called [SuperTurtle](https://github.com/cproctor/superturtle). To use SuperTurtle in this repo, we must install it using poetry. 
```shell
poetry install
```

{{< aside "Exiting the poetry shell" >}}
When you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}


{{< code-action "Take a look at the files inside with:" >}} `ls`
- `rotate.py`
- `scale.py`
- `translate.py`
- `interpolate.py`
- `framebyframe.py`
- `extension.py`
- `shapes.py`



---


## [2] Animations

There are many ways to animate still images! 

{{< columns >}}
{{< figure src="images/courses/cs9/unit00/lab_10_superturtle_rotate.gif" width="100%">}}
{{< figure src="images/courses/cs9/unit00/lab_10_superturtle_scale.gif" width="100%">}}
<--->
{{< figure src="images/courses/cs9/unit00/lab_10_superturtle_translate.gif" width="100%">}}
{{< figure src="images/courses/cs9/unit00/lab_10_superturtle_interpolate.gif" width="100%">}}
{{< /columns >}}

We're going to explore each type of animation by looking at some small mystery examples.


{{< code-action >}}{{< write-action >}} **Throughout this section, you will be asked to change part of the code and answer checkpoint questions about the following files:**
- `rotate.py`
- `scale.py`
- `translate.py`
- `interlopate.py`
- `framebyframe.py`
- `extension.py`


{{< code-action "Open the folder in Visual Studio Code:" >}}
```shell
code .
```

---

### Worksheet



{{< code-action  >}} ✏️ **Follow along with the worksheet for each file.** This will require you to run and edit code. 


---


## [3] Deliverables

{{< deliverables "For this lab, you should:" >}}
{{< write-action  >}} **Submit your worksheet with answers to each checkpoint question.**

{{< code-action "Push your code to Github" >}} 
0. `git status`
0. `git add -A` *(`-A` adds all changed files)*
0. `git status`
0. `git commit -m "describe changes here"` 
0. `git push`

{{< /deliverables >}}


