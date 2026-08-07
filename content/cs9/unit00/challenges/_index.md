---
title: "Challenges"
# bookCollapseSection: true
type: unit
# headless: true
numberHeaders: true
draft: true
---

# Challenges
Challenges will provide extra goals for students who have already finished
the assigned work and the extensions.
These challenges will require students to apply their coding skills in new ways.

Make sure you have followed the Initial Set Up before selecting a challenge. You are not required to work in order. Feel free to choose one that interests you. 

---

## Initial Set Up
 

{{< code-action >}} **Start by going into your `unit00_drawing` folder.**
```shell
cd ~/desktop/making_with_code/unit00_drawing/
```

{{< code-action "Then create a new folder:" >}}
```shell
mkdir challenges
```

{{< code-action "Now that you have a new folder, go into it." >}}
```shell
cd challenges
```
{{< aside "Important" >}}
When working on challenges, use the command **python3** to run your code. For example:

```shell
python3 turtle_art.py
```

{{< /aside >}}

---

## Turtle Art

**Your challenge is to choose one of the following patterns to recreate.**

{{< figure src="https://miro.medium.com/max/1400/1*rHXRb9HhOYNWoixmCD_SGQ.png" width="50%" alt-text="Stars" >}}


{{< figure src="https://media.geeksforgeeks.org/wp-content/cdn-uploads/20200717190249/python-turtle-spiral.png" width="50%" alt-text="Stars" >}}


{{< figure src="https://geekstand.top/wp-content/uploads/2020/02/image-13.png" width="50%" alt-text="Stars" >}}


{{< code-action "First, create a new file." >}} Make sure you are in your `/challenges` directory.
```shell
code turtle_art.py
```

{{< code-action "Copy and paste following into the top of your file to import the Turtle library at the start of the file:" >}}
```python
from turtle import *
```
{{< code-action "Start recreating!" >}} It's up to you customize the art however you'd like.


---

## Fibonnaci Sequence Visualization

**Your challenge is to create this classic visualization of the Fibonnaci sequence.**

{{< figure src="https://miro.medium.com/max/1400/1*c2eSLG6JnHLe8AZXjBrO7g.png" width="75%" alt-text="Stars" >}}


{{< code-action "First, create a new file." >}} Make sure you are in your `/challenges` directory.
```shell
code fibonnaci_visualization.py
```

{{< code-action "Copy and paste following into the top of your file to import the Turtle library at the start of the file:" >}}
```python
from turtle import *
```

{{< code-action "Code the fibonacci sequence." >}} If you have already completed this, you can simply copy and paste the code into your new file.

{{< code-action "Now, it's up to you to recreate the image to the best of your ability!" >}} If you have not yet figured out the solution to this problem, now is the tim

{{< code-action "Once you have this complete, add color!" >}} You may want to consider using the `modulo` to create a color pattern. You may also want to explore the [Random Library](https://docs.python.org/3/library/random.html) to random the colors.

---

## Stars

**Your challenge is to create the following image using turtle graphics.**

{{< figure src="images/courses/cs9/unit00/99_challenge_star.png" width="50%" alt-text="Stars" >}}


Before you begin, consider how you will break the larger problem down into sub-probems.
For example,
1. First try to create *one* star
2. Next try to create a *row* of stars
3. ...
4. ...

{{< code-action "First, create a new file." >}} Make sure you are in your `/challenges` directory.
```shell
code stars.py
```

{{< code-action "Copy and paste following into the top of your file to import the Turtle library at the start of the file:" >}}
```python
from turtle import *
```


{{< code-action "Now, it's up to you to recreate the image to the best of your ability!" >}}

---

## Pinwheel

Try to draw the a pinwheel with random colors, like the one below:

{{< figure src="images/courses/cs9/unit00/99_challenge_pinwheel_total.png" width="50%" alt-text="Stars" >}}

In order to build up to the entire pinwheel, you'll need a few helper functions. Start by creating a function that can draw kite shapes with any angle:

{{< figure src="images/courses/cs9/unit00/99_challenge_pinwheel_kites.png" width="50%" alt-text="Stars" >}}

Then, make a function that can add those kites together to make one of the spokes of the wheel:

{{< figure src="images/courses/cs9/unit00/99_challenge_pinwheel_spike.png" width="10%" alt-text="Stars" >}}

Create a function that draws a whole circle:

{{< figure src="images/courses/cs9/unit00/99_challenge_pinwheel_circle.png" width="50%" alt-text="Stars" >}}

If you want to include random colors, here's how:

{{< expand "Random Colors" >}}

```python
from random import randint # import random library
colormode(255) # change turtle color mode to rgb

color(100,200,200) # now you can set colors with numbers
red_val = randint(0,255) # create a random value between 0 and 255
color(red_val, 200, 200) # using the random red value in the color

```

{{< /expand >}}

