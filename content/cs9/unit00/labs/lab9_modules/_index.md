---
title: 09. Modules
draft: true
---

# Modules Lab

In this lab, we will learn how to organize our functions into modules. Modules are files of reusable function. You've already encountered modules before!

---

## [0] Setup

{{< code-action "Go into your" >}} `lab_modules` **folder:**

```shell
cd ~/Desktop/making_with_code/unit00_drawing/lab_modules_yourgithubusername
```
> Don't forget to change "yourgithubusername" to your actual Github username.

{{< code-action "Enter the Poetry shell:" >}}
```shell
poetry shell
```



---

## [1] What is a module?
In the previous lab, we used functions to break up a big program into smaller programs. Modules do the same thing, but on a larger scale!

So let's say you wrote a function in one file. What if you want to re-use a function you wrote in a different file? Copy it over?  It feels like there should be a better way.

**Today we are going to learn how to import code from one module into another.** But first, let's get some vocabulary straight:

- **All python code lives in `files` that end in `.py`.** They're just plain text files that you can edit using VS Code (or any text editor).
- **Python thinks of each file as a `module`.** Each module is its own little world.
- **Python thinks of each directory containing `.py` files as a `package`.** A package is a bundle of modules. So your `unit_00` directory is also a package.

---

### How to import a module
When you want to use something from another module, you need to `import` it.

We have actually already been doing this. Every one of our programs so far has started with `from turtle import *`. But what is this `turtle`? It's a module! And it lives in a file called `turtle.py` that some people wrote for you.


**There are actually three different ways to get `forward`.**

First, is the way you are used to doing it. This way imports all of the functions in `turtle.py`. It's quick and easy, but it's kind of sloppy and it's not always a very good idea.

```python
from turtle import *
forward(100)
```

Or, you can import just the `forward` function from `turtle`:

```python
from turtle import forward
forward(100)
```

Or, you can import the `Turtle` objects. *We will learn more about this in Unit 02: Games.*
You can import `turtle`:
```python
import turtle
turtle.forward(100)
```

---

**Imagine this scenario:**

```python
from bodily_functions import eat
from refrigerator import *
from trash_can import *

eat(chicken_sandwich)
```

You can see that the `eat` function came from `bodily_functions`, but where did that `chicken_sandwich` come from? The `refrigerator`? Or the `trash_can`? By importing just what we need from other modules, we can make it clear where everything came from, and we can make sure we don't import stuff we don't want. (What else did we import from the `trash_can`? Do we want that in our program?)

---

## [2] Tree

{{< code-action >}} **Let's start by going into `tree_drawing` folder.**
```shell
cd tree_drawing
```

This folder has 3 files:
- `basic_shapes.py`
- `tree_parts.py`
- `tree.py` 


{{< code-action "Open the folder in VS Code" >}}
```shell
code .
```

{{< look-action "Take a look at" >}} `basic_shapes.py` and `tree_parts.py`. Note how `tree_parts.py` uses functions from `basic_shapes.py`. Currently, the file `tree.py` is empty.

    
{{< code-action >}} **In `tree.py`, write a new function `tree_full()` to draw a full tree.** Your `tree_full()` function should be able to draw a tree of any size.

> Be sure to consider:
> - what modules will you need to import?
> - how can you combine exisiting functions to draw a full tree?
> - what parameters will `tree_full()` need, in order to draw at tree of **any size**?

When you run `tree.py` it should look like:

{{< figure src="images/courses/cs9/unit00/lab_09_modules_tree.png" width="30%" >}}

## [3] Deliverables

{{< deliverables  >}}

**Once you've successfully completed the tree drawing, be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSciiMuOg4kmZ1uEzZ7MtHwo2HFvzAIIhizuYMGf_WgdrcSWGA/viewform?usp=sf_link)**.

---

{{< code-action "Push your work to Github:" >}}
- git status
- git add tree.py 
- git status
- git commit -m "describe your drawing and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}

---

## [4] Extension: Forest

💻 **Write a function `forest()` that randomly draws trees around the screen!**

{{< figure src="images/courses/cs9/unit00/06_functions_forest.png" width="30%" >}}

As a reminder, here's how you can use the random library:
```python
from random import randint   # import the random library

x_coordinate = randint(-200,200) # generates a random integer between -200 and 200
y_coordinate = randint(-200,200)

goto(x_coordinate, y_coordinate) #moves the turtle to the random location
```

💻  **After you have your forest, try making the nearby trees larger than those farther away.**




---


## [5] Extension: Drawing Package

Now we are going to use a package full of fancy drawing functions to turbocharge your turtle.

Packages always include documentation to communicate how to use the included software.
**This lab will require you to read documentation** provided in the `README.md` file.

{{< checkpoint >}}

{{< look-action >}} **Open the [documentation](https://github.com/the-isf-academy/drawing/blob/master/README.md) for examples of all the functions available in the `drawing` package.** It has the following modules:
- `shapes.py`
- `movement.py`
- `lines.py`

{{< /checkpoint >}}


{{< code-action >}} **`cd` out of the `/tree` folder.**
```shell
cd ..
```

Here you should have:
- `/lab_modules`
  - `/drawing` package
  - `example_fancy_drawing.py` - an example usage of the drawing package
  - `fancy_drawing.py` -  an empty file for you to create your own drawing

---

### Example

{{< code-action "Start by running:" >}} `fancy_drawing_example.py`
```shell
python fancy_drawing_example.py
```
> *Consider:*
> - *Why does the drawing just appear?*
> - *What modules are used from the drawing package?*
> - *How do the colors repeat?*



{{< figure src="images/courses/cs9/unit00/lab_09_modules_fancydrawing.png" width="50%" >}}

{{< code-action "Experiment with editing the code." >}} Try make your own version of this pattern! Here is just one of many potential patterns:

{{< figure src="images/courses/cs9/unit00/lab_09_modules_example.png" width="50%" >}}

{{< look-action >}} Explore more color options [HERE](https://trinket.io/docs/colors)

---


### Fancy Drawing


{{< code-action >}} **In `fancy_drawing.py`, it is up to you to create a drawing of your choosing using the modules in the drawing package.** It must include uses of at least 3 different modules from the drawing package.
```shell
code fancy_drawing.py
```



{{< checkpoint >}}
**Be prepared to share your drawing!**
{{< /checkpoint >}}




---

<!-- ARCHIVE

## [2] Finding modules
There are three places you can import modules from:

- Some modules, like `turtle`, come pre-installed with python. When you import them, python knows where to find them.
- Some modules were published online by other software developers. If you install them, you can use them too.
  Like the built-in modules, python knows where to find these when you import them.
- Finally, any modules that are in the same directory as your python file can be imported.


Now let's try importing some of the code you wrote in previous lessons.

{{< code-action "Install" >}} `tree` to see what we're dealing with.
> **Don't forget to exit the Python shell by pressing `control+d` before entering this command! Check to make sure you see the command line prompt!**

```shell
brew install tree
```

Now, let's have a look at all your work in this class so far. We're going to show a tree of `.`, which means "here" (whatever directory you're currently in).

```shell
tree .
.
├── lab_00_terminal_adventure
│   ├── adventure
│   │   ├── seafloor
│   │   │   ├── coral_reef
│   │   │   │   ├── chest.py
│   │   │   │   └── reef.txt
│   │   │   ├── seafloor.txt
│   │   │   └── sunken_ship
│   │   │       ├── galley
│   │   │       │   └── ghost.py
│   │   │       ├── ship.txt
│   │   │       └── stateroom
│   │   │           └── desk.py
│   │   └── sinking.txt
│   └── returnToShip.py
├── lab_02.py
├── lab_02_drawing.py
├── lab_02_extension.py
├── lab_03_loops
│   ├── fibonacci_sequence.py
│   ├── geometric_sequence.py
│   └── loops_intro.py
├── lab_04_conditionals
│   ├── conditionals_modulo.py
│   └── conditionals_user_input.py
├── lab_05_while_loops
│   └── hailstone_sequence.py
└── lab_06_functions
    ├── grid.py
    └── ice_cream.py

```

From the `unit_00` folder, we can import any of these `.py` files as modules.

If they're in the same directory (like `lab_02_drawing.py`), we can just write `import lab_02_drawing`.

{{< code-action "Open the Python shell and try it:" >}}

```shell
python3
>>> import lab_02_drawing
```

Fond memories. You should have seen your responsive drawing run again. This is because when you import a module, all the code in that module runs.

What about subdirectories that contain `.py` files? Python thinks of these as packages. Remember that treasure chest from the It's buried a few layers deep in packages, but we can get it.


{{< code-action "Trying getting the chest from the " >}} `lab_00_terminal_adventure`

```shell
>>> import lab_00_terminal_adventure.adventure.seafloor.coral_reef.chest
```

Usually we use packages to group together code that belongs together. -->
