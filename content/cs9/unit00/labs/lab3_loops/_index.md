---
title: 03. Loops
# draft: true
---

# Loops Lab
In this lab, we will learn how to make the computer do the same instruction over and over.

In Python, when you want to run the same code multiple times, we use loops.
If you have used Scratch before, you have seen loops before:

{{< figure src="images/courses/cs9/unit00/03_loops0.png" width="200px" alt-text="Scratch loop" >}}

How does a loop work in python? Let's see.

---

## [0] Setup

{{< code-action >}} **Start by going into your `unit00_drawing` folder.**
```shell
cd ~/desktop/making_with_code/unit00_drawing/
```

{{< code-action "Then clone the lab" >}}
```shell
git clone https://github.com/the-isf-academy/lab_loops.git
```

{{< code-action "Now that you have the lab, go into its folder." >}}
```shell
cd lab_loops
```

{{< code-action "Enter the Poetry Shell to start the lab." >}} As a reminder, we will run this command at the start of each lab, but only when we are inside a lab folder.
```shell
poetry shell
```
{{< aside "Exiting the poetry shell" >}}
When you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}

{{< code-action "Take a look at the files inside with:" >}} `ls`
- `repetition.py`
- `square.py`
- `geometric_sequence.py`
- `extension_fibonacci_sequence.py`

---
## [1] How to loop
### Repetition

{{< code-action "Let's start by opening" >}} `repetition.py` **in Atom.**
```shell
code repetition.py
```

{{< code-action "Run your program and see what gets output:" >}}
```shell
python repetition.py
```

This loop runs 10 times, repeating everything indented to the right of the `for i in range(10):` line.
`i` is a variable that gets incremented by one every time the loop runs.

{{< code-action "Edit the code to make the loop run a different number of times." >}} Maybe 5 or 14.
Can you figure out how to do it?


{{< code-action "Edit the loop again to print the square of numbers 0-12." >}} *Remember, the square of a number, is the number multiplied by itself.*

When you run `python repetition.py` it should output:
```shell
0
1
4
9
16
25
36
49
64
81
100
121
144
```



<hr>

### Looping a Square


{{< code-action >}} **Use `code` to open `square.py`**

```shell
code square.py
```

Take a look at the code we've been using to draw a square:

```python
forward(100)
right(90)
forward(100)
right(90)
forward(100)
right(90)
forward(100)
right(90)
```

Pretty repetitive, right?

{{< code-action "Edit the code so that it uses a loop to draw a square, instead of repeating the same code over and over again." >}} 

{{< figure src="images/courses/cs9/unit00/03_loops3.png" width=25% alt-text="geometric drawing" >}}


---

## [2] Geometric Sequence

Loops are particularly useful when we need to do things over time. To see this, we're going to explore numerical sequences.


**Geometric sequences are sequences where there is a common ratio between each
number in the sequence.** A geometric sequence always begins with `1`. Each subsequent number in the sequence is calculated by finding the product of the number that precedes it and the ratio.


{{< figure src="https://www.storyofmathematics.com/wp-content/uploads/2021/01/geometeric-sequence-example.png" width="50%" alt-text="geometric sequence" >}}

> For example, `1, 2, 4, 16,...` is a geometric sequence
where each number is 2 times the number before it.
>
> The ratio between the sequence is 2

**In `geometric_sequence.py`, you will write a program that displays 10 digits of any geometric sequence and then visualizes the sequence in a drawing.**

---


### Pseudocode

**Pseudocode is an outline of the program we plan to write. When writing pseudocode, we don't worry about using Python syntax.** You can write in regular words to figure out the logic of the problem, then translate it into the correct syntax. 

{{< code-action >}} **To get started, open up `geometric_sequence.py`.**
```shell
code geometric_sequence.py
```

👀 **We have provided you with the pseudocode of the logic of the geometric sequence.** 
```python
# store the starting number, 1, in a variable called num 
# ask the user what the ratio should be and store it in a variable called ratio 
# loop 10 times 
    # print num
    # update the value of num to num + ratio 
```

{{< aside "FYI: Comments" >}}
If you don't want code to be executed when you run a program, you can comment it out by placing `#` at the beginning of the line.

This can be used as a debugging strategy or as a note-taking tool.
{{< /aside >}}

---

### Code

{{< code-action "After you are confident you understand the logic of the pseudocode, translate it into python code." >}} We suggest translating one line of pseudocode at a time.

Here is an example of what the program will output when run:
```shell
$ python geometric_sequences.py
What should the ratio of the sequence be? 4
1
4
16
64
256
1024
4096
16384
65536
262144
```

---

### Visualize the Geometric Sequence

Geometric Sequences are great for creating interesting visualizations.

{{< figure src="images/courses/cs9/unit00/03_loops1.png" width=40% alt-text="geometric drawing" >}}

{{< code-action "Using the Turtle library, create a visualization of the Geometric Sequence." >}} You may want to go back to `Lab 00. Turtle` for the list of Turtle commands. A few ideas:

- different size circles
- different colors
- a line chart 

{{< figure src="images/courses/cs9/unit00/03_loops2.png" width=40% alt-text="geometric drawing" >}}

---

## [3] Deliverables

{{< deliverables "When are you finished with the lab:" >}}

✔️   **Fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSdOWzsFMqW9hewAfyS6ayG1svFHvJngwxK0U53dbGBeOlAMhw/viewform?usp=sf_link)**

✏️  **Add a piece of your code and a screenshot to the `CS Year 1 Code Log` in your Google Drive.** Add a comment. You can:
> - ask a question about your code   
> - write a tip to your future self    
> - explain a bug you fixed in your code   
> - describe a piece of code you are proud of   


{{< /deliverables >}}

<hr>



## [4] Extension: Fibonacci Sequence

For the extension, explore a more complicated sequence, the Fibonacci sequence. This sequence has all kinds
of interesting properties.

The Fibonacci sequence begins with two numbers, `0` and `1`. Each subsequent number in the sequence is calculated by finding the sum of the two numbers that precede it.
> For example the first 5 digits of the sequence are:
> 0, 1, 1, 2, 3

**It is up to you to write the algorithm to determine the digits in the Fibonacci sequence.**

---

### Pseudocode

{{< code-action "Open the file:" >}}
```shell
code extension_fibonacci_sequence.py
```

{{< code-action >}} **In `extension_fibonacci_sequence.py`, use `comments` to write the pseudocode to calculate the first 10 digits of the Fibonacci sequence.**

---

### Code
{{< code-action "After you are confident your pseduocode has the correct logic, translate it into Python code." >}}

Here is an example of what the program will output when run:
```shell
$ python extension_fibonacci_sequence.py
0
1
1
2
3
5
8
13
21
34
```

---

### Visualize the Fibonacci Sequence

Use your working code to draw a pattern that utilizes the Fibonacci sequence.

{{< figure src="images/courses/cs9/unit00/03_loops4.png" width=40% alt-text="geometric drawing" >}}



{{< code-action "First, use your Fibonacci code to draw a single spiral." >}}  You can do this by drawing a
line for each number in the Fibonacci sequence and connecting the lines at a consistent angle.

{{< figure src="images/courses/cs9/unit00/03_loops5.png" width=20% alt-text="geometric drawing" >}}


#### Multiple spirals
{{< code-action "Loop the drawing code to draw multiple spirals originating from the center." >}}

Now, the Turtle should draw something like this:

{{< figure src="images/courses/cs9/unit00/03_loops6.png" width=40% alt-text="geometric drawing" >}}

{{< aside "FYI: Moving the Turtle" >}}
You can return your turtle to the center of the window using `goto(0, 0)`. You can also use `penup()` and `pendown()` to keep the turtle from drawing as it returns to the
center.
{{< /aside >}}

#### Clockwise and counterclockwise
To get a pinecone or flower effect, you can try spiralling clockwise
and counterclockwise.

{{< code-action "Repeat your spiral code, changing it to make your spirals turn in the other direction." >}}

Feel free to add colors and personalize the visualization however you would like!
