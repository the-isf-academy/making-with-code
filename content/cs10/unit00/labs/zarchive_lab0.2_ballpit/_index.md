---
title: "0.1 Review: Ball Pit"
weight: 30
draft: true
---

# Ball Pit

In this lab, we'll get re-aquainted with CS concepts such as classes and inheritance with the Turtle library. 

{{< expand "Extra Resouces: Learn more about Python Classes" >}}
- Creating a Class: [Python Classes](https://www.w3schools.com/python/python_classes.asp)
- Inheritance: [Python Inheritance](https://www.w3schools.com/python/python_inheritance.asp)
{{< /expand >}}


--- 

## [0] Set up


{{< code-action "Let's start by cloning the repository" >}} in your `unit03_networking` folder.  Be sure to change `yourgithubusername` to your actual Github username.

```shell
cd ~/desktop/making_with_code/unit03_networking
git clone https://github.com/the-isf-academy/lab_ballpit_yourgithubusername
cd lab_ballpit_yourgithubusername
```
> 🤔 *Remember, `tab` autocompletes files and folders in the Terminal*

📄 **This repository contains the following files:**
- `ball.py`
- `animation_ballpit.py`

{{< code-action "Enter the Poetry Shell." >}} 
```shell
poetry shell
```
---

## [1] Exploring Ball Pit


{{< code-action >}} **Run `animation_ballpit.py` to see the Ballpit animation.**
 
```shell
python animation_ballpit.py
```


{{< figure src="images/courses/cs10/unit00/lab0.2-00.gif" width="50%" >}}

In the Ballpit, notice each ball has a different size, stays the same size the whole time, and bounces off the walls.

{{< code-action >}} **Let's delve into the code.** Start by looking at `animation_ballpit.py`
```shell
code .
```

{{< code-action >}} **Change the number of Balls that are in the Ballpit.** 

{{< figure src="images/courses/cs10/unit00/lab0.2-01.png" width="50%" >}}


{{< code-action >}} **Now, let's focus on `ball.py` and the method `set_color()`. Change `set_color()` so the color is a random shade of green.** Or, feel free to change it to any other color!
> 🧐 *You may need to look around the file for an example of how to use the Random library*

{{< figure src="images/courses/cs10/unit00/lab0.2-02.png" width="50%" >}}


---

## [2] Inheritance 

What if we wanted to add different types of Balls to the Ballpit? For example, what if we wanted some of the Balls to change size as they moved? 

We can use **inheritance**!

---

### BreathingBall

`BreathingBall()` is a child class of `Ball()` that grows and shrinks as it moves. It looks like it's breathing in and out.

It **inherits** all of the **methods** from `Ball()` and **overrides** the `update()` method. 

{{< code-action >}} **Copy and paste the code below into the bottom of `ball.py`**

```python
class BreathingBall(Ball):
    # BreathingBall extends the Ball class.
    # A BreathingBall is the same as a Ball,
    # but it grows and shrinks as it moves.

    def __init__(self):
        # This constructor calls the constructor of the parent class,
        # and adds a step variable.
        
        super().__init__()
        
        self.step = random.randint(0,120)
        
    def update(self):
        # Calls the parent method and also changes the size of the ball
        
        super().update()

        self.step += 1
        new_radius = math.sin(self.step/20)*(3/2)+1.5
        self.set_size(new_radius)
```

{{< code-action >}} **Add the `BreathingBall()` to the Ballpit.**
> 🧐 *What lines of code will you need to add to `animation_ballpit.py`?*

{{< figure src="images/courses/cs10/unit00/lab0.2-03.gif" width="50%" >}}

---

### Override a Method

Currently, it's pretty difficult to notice the regular `Ball()` from the `BreathingBall()`. Let's change that by overriding `set_color()` in `BreathingBall()`

{{< code-action >}} **In `ball.py` under the `BreathingBall()`, override the method `set_color()`.** 
> 🧐 *Remember, `update()` is another function in `BreathingBall()` that is overridden from `Ball()`*


{{< figure src="images/courses/cs10/unit00/lab0.2-04.png" width="50%" >}}

🎨 **Feel free to customize your BallPit however you'd like!** For example, `bgcolor('red')` changes the background color of the screen to the color red. 

---


## [3] Deliverables



{{< deliverables >}}  

Once you've successfully completed the lab, fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSdMNcCkoniPqOsigzroaEyhCcLDNCbICICmUmMQ7ElK3d0CXw/viewform?usp=sf_link).


{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push
{{< /deliverables >}}


---

## [4] Extension: Increase the Chaos

If time allows, ramp up the chaos even further!


{{< code-action >}} **Add in a `WarpBall()`**. It warps around to the opposite side of the screen.

```python
class WarpBall(Ball):
    # WarpBall extends the Ball class.
    # A WarpBall is the same as a Ball,
    # but instead of bouncing off the wall,
    # it reappears on the other side of the screen.

    def __init__(self):
        super().__init__()

    def update(self):
        # Checks whether the ball has hit a wall.
        # If the ball has hit a wall, it "warps" the ball
        # onto the opposite side of the screen        

        if self.x > 1:
            self.x = 0
        if self.y > 1:
            self.y = 0
```

{{< code-action "Embrace the chaos of the ball pit! Cause the Ball, WarpBall, and BreathingBall to change color as they move." >}} 

{{< figure src="images/courses/cs10/unit00/lab0.2-02.gif" width="400px" >}}


{{< code-action  >}} **Create your own type of `Ball()` or a whole new shape - like a `Square()`!** 

{{< figure src="images/courses/cs10/unit00/lab0.2-01.gif" width="400px" >}}

{{< aside >}}
If you want to use an inherited method while also changing some behavior, you can do that like this:
```python
def update(self):
    super().update()        # this calls the inherited behavior
    self.turtle.right(5)    # any new code will be run afterwards
```
{{< /aside >}}

{{< code-action "Be sure to push any extension changes you make to Github!" >}}