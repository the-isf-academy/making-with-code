---
title: "0 Turtle"
weight: 10
---

# Review: Turtle Drawing

Welcome to Year 2 CS! We hope you're excited for what we have planned this year 😄

Let's review by taking it back to Turtle drawings!

---

## [0] Set up

Now that you're in **Year 2** you need a new unit folder.

{{< code-action  >}} **Start by opening your Terminal!**

{{< code-action  >}} **In the Terminal, go into your `making_with_code` folder and create a `unit03_networking` folder.** If you no longer have a `making_with_code` folder, you will need to create one. 

```shell
cd ~/desktop/making_with_code
mkdir year2_review
cd year2_review
```


{{< code-action "Then, clone your starter code." >}} Be sure to change `yourgithubusername` to your actual Github username.
> *remember: `tab` autocompletes in the Terminal*

```shell
git clone https://github.com/the-isf-academy/lab_turtle_review_yourgithubusername
```

{{< code-action >}} `cd` **into the lab**
```shell
cd lab_turtle_review_yourgithubusername
```


{{< aside "Windows Users" >}}

We suggest not copying the path command, and instead using `cd` and `ls` to ensure you are in the correct `making_with_code` folder.

{{< /aside >}}

{{< code-action "Install Tkinter" >}} We'll need this for our drawings.
```shell
brew install python-tk
```

{{< code-action "Enter the Poetry Shell." >}} Remember, we run this command at the start of each lab, but only when we are inside a lab folder.
```shell
poetry shell
```
{{< aside "Exiting the poetry shell" >}}
When you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}



---

## [1] Create a Turtle Drawing

{{< code-action "Run the Python file" >}} 
```shell
python turtle_drawing.py
```

{{< code-action "Open the code." >}} The `.` opens the entire folder.
```shell
code . 
```

{{< code-action >}} **Using the starter code in `turtle_drawing.py` create a drawing that includes at least 3 of CS concepts below:**

- [Variables](https://www.w3schools.com/python/python_variables.asp)
- [Loops](https://www.w3schools.com/python/python_for_loops.asp)
- [Conditionals](https://www.w3schools.com/python/python_conditions.asp)
- [Lists](https://www.w3schools.com/python/python_lists.asp)
- [Dictionaries](https://www.w3schools.com/python/python_dictionaries.asp)
- [Functions with arguments](https://www.w3schools.com/python/python_functions.asp)

{{< figure src="https://freshgadgets.nl/wp-content/uploads/2014/12/inspirograph2.jpg" width="50%">}}

---

### A Few Helpful Functions

- 🌈 Explore color options [here](https://trinket.io/docs/colors)

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
| setheading  |       angle      |   `setheading(90)`   | Sets the pen to the 0th degree                                |
| circle  |       size      |   `circle(10) `  | Sets the radius of the circle                                                                                            |
| goto  |       x, y      |   `goto(90,0) `  | Moves turtle to a given coordinate                                                 |
| begin_fill  |       None     |  `begin_fill()`  | Marks the start of the color fill       |
| end_fill  |       None     |   `end_fill()`   | Marks the end of the color fill           |
| fillcolor  |       colorname     |   `fillcolor('purple') `  | Sets the color of the fill          |



## [2] Deliverables


{{< deliverables  >}}

🤔 **Remember, at the end of each class we push to *Github***

{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your drawing and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}
