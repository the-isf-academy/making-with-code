---
title: 02. Variables

draft: true

---

# Variables Lab
In this lab, we will learn about variables, a powerful storage container of information.

{{< aside "FYI" >}}
You may **move at your own pace** during labs. We expect ***all* students to complete the work up to the deliverables** section. 

There are always extension activites for students to continue exploring a topic after the deliverables form. 

{{< /aside >}}


---

## [0] Setup


{{< code-action >}} **First, let's use `cd` to go into our unit directory.**
```shell
cd ~/Desktop/making_with_code/unit00_drawing
```

{{< code-action >}} **Now, let's *clone* the lab.** This pulls the code from the cloud, onto your local computer. We will do this at the start of each lab.
```shell
git clone https://github.com/the-isf-academy/lab_variables
```


{{< code-action "Install Tkinter" >}} We'll need this for our drawings.
```shell
brew install python-tk
```

{{< code-action >}} **Then, enter the lab folder and start the `poetry shell`**
```shell
cd lab_variables
```


```shell
poetry shell
```


{{< aside "Exiting the poetry shell" >}}
When you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}

{{< code-action "Take a look at the files inside with:" >}} `ls`
- `variable_test0.py`
- `variable_test1.py`
- `variable_test2.py`
- `responsive_drawing.py`

---

## [1] Variable Tests


### Variable test 0

{{< code-action "First let's run" >}} `variable_test0.py`.
> *You may need to type `python3` instead of `python`*
```shell
python variable_test0.py
```

👀 **You should see the following words print out in the Terminal.**
```shell
Hello
YOUR NAME
```

{{< code-action "Let's see how that is happening by opening the file in Visual Studio Code:" >}} `code variable_test0.py`
> VSCode is the code editor we will be using throughout this course.

```python
# variable_test0.py

name = "YOUR NAME"
print("Hello")
print(name)
```

{{< code-action >}} **Start by replacing*** `"YOUR NAME"` ***with your name (but keep the `""`).** Now you have *declared* the `name` variable and *assigned* your name as its value.

{{< code-action "Save the file and run the program again." >}} You should see an output similar to the one below:
> *Tip: Use the up arrow to cycle through your previous commands in Terminal*

```shell
$ python variable_test0.py
Hello
Emma
```

What just happened? After storing your name in the `name` variable, `print(name)` prints out whatever is stored in the variable.

Let's do another test.

{{< code-action "Add the following lines of code to your file." >}}

```python
name = "YOUR FRIEND'S NAME"
print("HELLO")
print(name)
```

{{< code-action >}} **Replace** `"YOUR FRIEND'S NAME"` **with your friend's name.**

Now our program is printing the `name` variable twice but we've assigned different values to the
variable at different places in the code. What do you think will happen?

{{< code-action "Run the code to find out!" >}} You should see an output similar to the one below:
```shell
$ python variable_test0.py
Hello
Emma
Hello
Britte

```
---

### Variable test 1

{{< code-action "Let's continue explore variables by running a different variable test:" >}} `python variable_test1.py`

Hmm, something is wrong here.

{{< code-action "Open up the code and try to fix the bug:" >}} `code variable_test1.py`
> *Be sure to read the error message. Why does it say `'favorite_fruit' is not defined`?*
```python
# variable_test1.py

favorite_color = "color"
print("Your favorite color is " + favorite_color)
print("Your favorite fruit is " + favorite_fruit)
favorite_fruit = "fruit"
```


---

### Variable test 2
{{< code-action "Now, let's experiment with user input. Run the 3rd variable test:"  >}} `python variable_test2.py`

```python
# variable_test2.py

favorite_artist = input("What is your favorite artist? ")
print("Oh, I love " + favorite_artist + "!")
```

{{< code-action "Run your program multiple times and change up what artist you type." >}}

This shows how your programs can be responsive to user input and how you can store
information from the user in variables that may change every time your program runs.


---


## [2] Responsive Drawing


The last variable test showed how your programs can be responsive to user input and how you can store information from the user in variables that may change every time your program runs.

**This means that we can use variables to make our code do different things at different times based on input.** Can you imagine how that might help use make more interesting turtle drawing?

{{< figure src="images/courses/cs9/unit00/02_variables0.png" width="30%" alt-text="blue hexagon" >}}

{{< code-action >}} **Run the file `responsive_drawing.py` and enter a number in the Terminal.** Notice, the drawing changes based on your input!

{{< figure src="images/courses/cs9/unit00/02_variables1.png" width="30%" alt-text="blue hexagon" >}}


{{< code-action "Create a turtle drawing that is responsive to user input." >}} Open the file `responsive_drawing.py` to get started. Your drawing should have at least: 
- 1 numerical user input
- 1 word based user input


{{< aside "FYI" >}}
You can get input from the user while your program is running using `input("PROMPT")`. By default, `input("PROMPT")` collects words.

If you want to get a number from the user, use `int(input("PROMPT"))`. This is because
Python treats numbers and words differently. We'll talk more about this next unit.

*For example:*
```python
name = input("What is your name? ")
age = int(input("How old are you? "))
```

{{< /aside >}}


📖 Be sure to reference the Turtle commands in `00. Turtle`. You can also find additional Turtle functions by looking at the [official documentation](https://docs.python.org/3/library/turtle.html).

---

## [3] Deliverables


{{< deliverables  "Once you've successfully completed the responsive drawing:" >}}

✔️   **Fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLScsVvy1k4qOm4MHAYpliMpBdXSiNsCG25tvrDvz6i6YMf7FUQ/viewform?usp=sf_link)**

✏️  **Add a piece of your code and a screenshot to the `CS Year 1 Code Log` in your Google Drive.** Add a comment either asking a question about your code OR describing a piece of code you are proud of. 


{{< /deliverables >}}

---

## [4] Extension: Randomness


**Add randomness to your drawing!** For this, you will need to use the [random library](https://docs.python.org/3/library/random.html).  

{{< code-action >}} **At the top of your file, import the `randint()` function from the random library.**
```python
# responsive_drawing.py

from turtle import *
from random import randint
```

**`randint()` generates a random integer between two numbers.** For example, bellow will generate an integer between 1 and 100:
```python
randint(1,100)
```


<!-- 

For example, if the user inputs `1` the face should be an average size. If the user inputs `.5`, the face should be half size. If the user inputs `2`, the face should be twice the size.


{{< code-action "Create a new file:" >}} `code size_factor.py`.
> *Make note of how we create a new file.* `code file_name.py` -->
