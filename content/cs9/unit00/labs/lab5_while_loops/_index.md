---
title: 05. While Loops

draft: true
---

# While loops

In addition to `for` loops which run for a set number of iterations, Python has another type of loop. `while` loops iterate until a particular condition is met.

---

## [0] Set up


{{< code-action "Start by going into the unit folder." >}}
```shell
cd ~/desktop/making_with_code/unit00_drawing/
```

{{< code-action "Then clone the lab" >}}
```shell
git clone https://github.com/the-isf-academy/lab_while.git
```


{{< code-action "Now that you have the lab, go into its folder." >}}
```shell
cd lab_while
```

{{< code-action "Enter the Poetry Shell to start the lab." >}} As a reminder, we will run this command at the start of each lab, but only when we are inside a lab folder.
```shell
poetry shell
```

{{< aside "Exiting the poetry shell" >}}
When you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}

{{< code-action "Take a look at the files inside with:" >}} `ls`
- `guessing_game.py`
- `hailstone_sequence.py`

---


## [1] What is a While Loop?


**`while` loops use conditions just like `if` statements.** You can use operators to compare
values or to generate `True` or `False` conditions. Looping until a condition is met
can be useful when you are getting input from a user, generating random variables,
or repeatedly changing a value.

```python
user_input = -1
while user_input < 1 or user_input > 10:
    user_input = int(input("Tell me a number between 1-10 (inclusive): "))

```

---

## [2] Guessing Game

One common usage of `while` loops is in games. In this first part of the lab, you will be using a `while` loop to create a number guessing game.




{{< code-action "Start by running the game file:" >}}
```shell
python guessing_game.py
```


```shell
----------------------------
Guess a number between 1-10!
----------------------------

Guess a number: 5
Guess a number: 10
Guess a number: 3
Correct
Guess a number: 8
Guess a number:
```
> It works! But, even after you guess the correct number, the game continues. It's up to you to fix the code!

{{< aside "Stopping a program" >}}
When you want to stop running a program, type `^C` in the terminal.
{{< /aside >}}

{{< code-action "Open the file in Visual Studio Code" >}}
```shell
code guessing_game.py
```

{{< code-action "Fix the game so the loop ends once the user guesses the correct number. It should also tell the user if their guess is too high or too low." >}}


{{< figure src="images/courses/cs9/unit00/05_while_guessing_game.drawio.png" width=50% alt-text="bubble tea flow chart" >}}


👾 **The final game should like something like this:**
```shell
----------------------------
Guess a number between 1-10!
----------------------------

Guess a number: 5
Too high...
Guess a number: 3
Too high...
Guess a number: 2
Correct
```

---



## [3] Hailstone Sequence

Now that you've gotten practice with `while` loops, **you will be exploring a special sequence known as the
hailstone sequence**.

**This sequence results from the following rules** (known as the Collatz conjecture):
- take any positive number `n`
- find the next term of the sequence using the following rules:
    - if `n` is even, the next term is `n/2`
    - if `n` is odd, the next term is `n*3+1`
- repeat until `n = 1`

The conjecture states that no matter the starting value of `n`, the sequences will always reach 1.

This sequence is interesting because though no number has ever been found that doesn't reach 1,the Collatz conjecture has never been proven. **This is an unsolved problem in mathematics!**

{{< figure src="images/courses/cs9/unit00/05_while_hailstone.drawio.png" width=50% alt-text="bubble tea flow chart" >}}


---

### Pseudocode the Sequence

This is another algorithm which will require pseudocode to figure out.

✔️ **Your program must:**

0. Ask the user what number the program should calculate the hailstone sequence of.
0. Print out each number in the sequence.
0. Print out how many steps it took for the sequence to reach `1`


🤔  **Here are some things to consider:**
- This program will require a loop. What kind of loop do you think is best? 
    - *Remember that for loops run for a definite number of times and while loops run until a condition is met.*
- You will need to determine if each term is odd or even. 
    - What are some characteristics of even numbers that will help you determine if a number is even?
- In addition to calculating each term, you must count how many steps it takes to reach 1 and report this number at the end.


{{< code-action >}} **To get started, open up `hailstone_sequence.py`.**
```shell
code hailstone_sequence.py
```

{{< write-action >}} **Use `comments` to complete the pseudocode to find the hailstone sequence of any starting number.** There are currently three lines of pseudocode in the file.
> *A comment is any line that starts with a `#`*
>
> `# this is a comment`
>
> *You can comment code quickly by highlightly multiple lines and clicking `⌘+?` - this will comment or uncomment code.*


---

### Code the Sequence

{{< code-action "Translate your pseudocode into Python code." >}} Once completed, your program will look something like this:
```shell
--- Hailstone Sequence ---

Input a starting number: 21
64
32
16
8
4
2
1
It took 7 steps to complete the sequence
```



---

## [4] Deliverables

{{< deliverables  >}}

**Once you've successfully completed the sequence be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLScUoRxMYShhj2xg2fKdqbJ9FbkPwj15VNd0oqguKE-eGjEkzg/viewform?usp=sf_link)**.

✏️  **Add a piece of your code and a screenshot to the `CS Year 1 Code Log` in your Google Drive.** Add a comment. You can:
> - ask a question about your code     
> - write a tip to your future self    
> - explain a bug you fixed in your code   
> - describe a piece of code you are proud of   

{{< /deliverables >}}

---

## [5] Extension: Visualizing the Sequence
The sequences you formed above are known as hailstone sequences, because the terms move up
and down but ultimately reach 1 like hailstones gaining layers of ice in a cloud.


{{< figure src="images/courses/cs9/unit00/05_while_hailstone_cloud.png" width="50%" title="Hailstones forming in a cloud" >}}

This pattern can lead to some interesting visualizations of hailstone sequences.

{{< code-action "Use your hailstone sequence code to create a visualization for the hailstone sequence using Turtle." >}}

You can visualize the terms in a sequence starting with a specific number:
{{< figure src="images/courses/cs9/unit00/05_while_hailstone_terms.png" width="50%" title="Terms in hailstone sequence starting at 590" >}}

Or you can visualize the number of steps it takes to reach one from a set of integers:
{{< figure src="images/courses/cs9/unit00/05_while_hailstone_steps.png" width="50%" title="Steps to reach one in hailstone sequence as radii of half circles for integers 1-100" >}}



<br>

{{< code-action "Add a random color element to the visualization" >}}

You will need to reference the following:
- [Turtle Color Documentation](https://docs.python.org/3/library/turtle.html#turtle.color)
- [Python Random Library Documentation](https://docs.python.org/3/library/random.html)

At the top of the file, you must to change the color mode to 255.

```python
colormode(255)
```

You can then use the RGB color system. For example `color(0,0,255)` is pure blue.
```python
color(0,0,255)
```