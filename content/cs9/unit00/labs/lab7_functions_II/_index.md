---
title: 07. Functions II
draft: true
---
# Functions Lab | Part II

In this lab, we will deepen our understanding with a series of design challenges.

---

## [0] Set up

{{< code-action "Start by going into the unit folder." >}}
```shell
cd ~/desktop/making_with_code/unit00_drawing/
```

{{< code-action "Then clone the lab" >}}
```shell
git clone https://github.com/the-isf-academy/lab_functions2.git
```

{{< code-action "Now that you have the lab, go into its folder." >}}
```shell
cd lab_functions2
```

{{< code-action "Enter the Poetry Shell to start the lab." >}} As a reminder, we will run this command at the start of each lab, but only when we are inside a lab folder.
```shell
poetry shell
```

{{< aside "Exiting the poetry shell" >}}
When you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}

---

{{< code-action "Open the file:" >}}
```shell
code circle_patterns.py
```
{{< look-action "Take a look at the code inside" >}}

```python
from turtle import *

def filled_circle(circle_size,circle_color):
    fillcolor(circle_color)
    begin_fill()
    circle(circle_size)
    end_fill()

```


### [Helpful Turtle Functions]

Here are some helpful Turtle functions that may make this problem easier. You are not required to use all of these functions.

| Function |       Input      |   Example Use  | Explanation                                                                                                                      |
|:--------:|:----------------:|:--------------:|----------------------------------------------------------------------------------------------------------------------------------|
|  forward |      amount      |  `forward(100)`  | Moves the turtle forward by the specified amount                                                                                 |
| backward |      amount      |  `backward(100)` | Moves the turtle backward by the specified amount                                                                                |
|   right  | angle in degrees |    `right(45)`   | Turns the turtle clockwise by the specified angle                                                                                |
|   left   | angle in degress |    `left(45)`    | Turns the turtle counter clockwise by the specified angle                                                                        |
|   color  |     colorname    |  `color('red') ` | Sets the color for drawing. Use "red", "black", etc.  [Here's a list of all the colors](https://trinket.io/docs/colors).                                           |
|   speed  | number from 0-10 |    `speed(0)`    | Determines the speed at which the turtle moves around the window. 1 for slowest, 3 for normal speed, 10 for fast, 0 for fastest. |
|  pendown |       None       |    `pendown()`   | Puts down the turtle/pen so that it draws when it moves                                                                          |
|   penup  |       None       |    ` penup()`    | Picks up the turtle/pen so that it doesn’t draw when it moves                                                                    |
| pensize  |       width      |   `pensize(4)`   | Sets the width of the pen for drawing                                                                                            |
| setheading  |       angle      |   `setheading(90)`   | Sets the orientation of the turtle to an angle. 0 is east; 90 is north; 180 is west; 270 is south                                |
| circle  |       size      |   `circle(10) `  | Sets the radius of the circle                                                                                            |
| goto  |       x, y      |   `goto(90,0) `  | Moves turtle to a given coordinate                                                 |
| begin_fill  |       None     |  `begin_fill()`  | Marks the start of the color fill       |
| end_fill  |       None     |   `end_fill()`   | Marks the end of the color fill           |
| fillcolor  |       colorname     |   `fillcolor('purple')`  | Sets the color of the fill          |
| pencolor  |       colorname     |   `pencolor('purple')`  | Sets the color of the pen          |
| bgcolor  |       colorname     |   `bgcolor('black')`   | Changes the background of the turtle screen           |
| colormode  |       colorname     |   `colormode(255)`  | Changes the turtle color to accept rgb colors.  e.g. color(255,15,23)          |




---

## [1] Circle Patterns

This mini lab is designed to be a pick and choose adventure. The patterns below are in order of difficulty. It is up to you to **choose patterns that are at an appropriate level of difficulty for you**.

**Each of the patterns rely on the `filled_circle()` function provided in the starter code.**


{{< aside "Commenting Code" >}}

It can be incredibly useful to use comment code! Comments are useful for
- leaving yourself notes
- leaving others notes 
- isolating testing 

```python
# this is a comment
# print('hello')
```

In visual studio code, **you can select one or multiple lines of code and press `⌘+?` to comment or uncomment code**.

{{< /aside >}}

---

### Alternating Pattern


{{< figure src="images/courses/cs9/unit00/lab_08_functions_00.png" width="50%">}}

{{< code-action >}} **Code a function `alternating_pattern(num_circles)`**
> *Example function call: `alternating_pattern(5)`*
   - It takes `num_circles` as a parameter - this will change the amount of circles in the pattern
   - Hard code the 2 colors to alternate between
   - *Hint: look at the conditionals lab*

For an additional challenge:
- add `num_circle_size` as a parameter - this will change the size of the circles in the pattern
   - *Example function call: `alternating_pattern(5,200)`*

---

### Bullseye

{{< figure src="images/courses/cs9/unit00/lab_08_functions_01.png" width="50%">}}


{{< code-action >}} **Code a function `bullseye_pattern(num_circles, starting_circle_size)`**
> *Example function call: `bullseye_pattern(5, 200)`*

   - It takes `num_circles` and `starting_circle_size` as parameters - the number of circles and the size of the bullseye should adjust accordingly
   - Hard code the 2 colors to alternate between

For an additional challenge:
- add `color1` and `color2` as parameters - this will change the colors of the pattern.
   - *Example function call: `bullseye_pattern(5, 200, 'coral', 'light blue')`*

---

### Size Pattern
{{< figure src="images/courses/cs9/unit00/lab_08_functions_02.png" width="50%">}}

{{< code-action >}} **Code a function `size_pattern(num_columns, num_rows, color)`**
> *Example function call: `size_pattern(6,5,'coral')`*

- It takes `num_columns`, `num_rows`, and `color` as parameters

---

### Half-tone Pattern

{{< figure src="images/courses/cs9/unit00/lab_08_functions_03.png" width="50%">}}

{{< code-action >}} **Code a function `halftone_pattern(num_columns, num_rows, color1, color2)`**
> *Example function call: `halftone_pattern(6,5,'dark blue','light blue')`*

- It takes `num_columns`, `num_rows`, `color1`, and `color2` as parameters

---

### Random Pattern

{{< figure src="images/courses/cs9/unit00/lab_08_functions_04.png" width="50%">}}

{{< code-action >}} **First, code a function `thick_circle(circle_size, circle_color, thickness)`**
- It should draw a circle of any color, size, and any pen thickness

{{< code-action >}} **Second, code a function `random_pattern(num_circles, background_color)`**
> *Example function call: `random_pattern(20,'black')`*

- It should create a random pattern of thick circles and filled circles
- The circles should all be of random colors and sizes.


**This will require you to:**
-  use the `randint()` function from the random library
   - add `from random import randint` to the top of your file
- change the color mode to accept rgb colors
   - add `colormode(255)` to the start of the function

---

## [2] Deliverables

{{< deliverables  >}}

☑️ **At then end of class, be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLScQ0UNGAqfkqzX-REmYEKfwTCHaBjrDPB8uKybkxJk4-wp_kQ/viewform?usp=sf_link)**.


✏️  **Add a screenshot of a code snippet to your `CS9 Lab Code Log` in your Google Drive.** Add a comment with a key takeaway, a question about your code, or describing a piece of code you are proud of. 


{{< /deliverables >}}
