---
title: 0. Typing Game
type: lab
slug: lab_typing_game
repo_url: https://github.com/the-isf-academy/lab_typing_game
init_action: create_from_template 
numberHeaders: true
# draft: true
---

# Typing Game

In this lab, you will create a typing game! You will be re-introduced to the Terminal, Python syntax, and logical flow.


{{< code-action "Let's start by playing: " >}} [MonkeyType](https://monkeytype.com/)

{{< figure src="images/courses/cs9/unit02/00_monkey_type.png" width="100%" >}}

<!-- {{< write-action "Once you understand the game, re-arrange the pseudocode in the correct order." >}} Check with a teacher before moving on to the setup.  -->


---


## [0] Setup

{{< code-action "In the Terminal, open your" >}} `making_with_code` **folder:**
```shell
cd ~/desktop/making_with_code
```

{{< code-action "Create a new folder for the unit:" >}}
```shell
mkdir unit02_games
```

{{< code-action "Clone your repository with starter code for the lab:" >}}
> replace the `yourGithubUsername` with your Github username.
>
> *example: `git clone https://github.com/the-isf-academy/project_animation_emmaqbrown`*


```shell
git clone https://github.com/the-isf-academy/lab_typing_game_yourGithubUsername
```

{{< code-action >}} `cd` **into the lab**
```shell
cd lab_typing_game_yourGithubUsername
```

<!-- 
{{< aside "Windows Users" >}}

I suggest not copying the path command, and instead using `cd` and `ls` to ensure you are in the correct `making_with_code` folder.

{{< /aside >}} -->

{{< code-action "Enter the Poetry Shell." >}} We will also run this command at the start of each lab, but only when we are inside a lab folder.
```shell
poetry shell
```
{{< aside "Exiting the poetry shell" >}}
When you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}

{{< code-action "Take a look at the files inside with:" >}} `ls`
- `typing_game.py` - will run the game
- `prompts.py` - stores the typing prompts
- `helpers.py.` - helper functions for the games

<!-- {{< code-action "Open the folder in Visual Studio Code: " >}} `code .` -->
<!-- > In the Terminal, We will use `code` now instead of `atom` -->
--- 

## [1] Typing Game

{{< code-action "Start by running the game: " >}} `python typing_game.py`. As you can see the welcome screen, rules, and countdown to the start of the game already coded. Now that you understand how the logical flow of the game, it's up to you to finish it!

{{< look-action "A successful game should run like this:" >}} 

{{< figure src="images/courses/cs9/unit02/00_typing_game_ex1.png" width="100%" >}}

---

### Game Logic

{{< code-action "Open the folder in Visual Studio Code:" >}}
```shell
code .
```

{{< code-action "Translate the pseudocode to Python code in" >}} `typing_game.py`. The pseudocode is in the correct order in the comments of the file. 
 

{{< aside "Be sure to constantly test your game!" >}}

Run your game after every change you make to the code: `python typing_game.py`

Testing is the key to successful debugging!
{{< /aside >}}

---

{{< look-action >}} **Here are a few useful functions you will need to successfully code a working typing game:**

`input()`
- parameters: string 
- return value: what user types in the terminal
```python
user_answer = input("Do you like pizza? (yes/no): ")
```

`choice()` - *[random library](https://docs.python.org/3/library/random.html)*
- parameter: a list
- return value: a random item from a list
```python
animal_list = ['dog','cat','bird']
random_animal = choice(animal_list)
```

`time()` - *[time library](https://docs.python.org/3/library/time.html#time.time)*
- return value: the current time
```python
current_time = time()
```

`calculate_wpm()` - *this function is written in `helpers.py`*

- parameters: `prompt`, `start_time`, `end_time`
- return value: the words per minute
```python
wpm = calculate_wpm('hello i am a dog', start_time, end_time)
```

`round()`
- parameters: number to round, number of decimal places
```python
number_rounded = round(2.555,2)
```

---

### Calculate Accuracy

Now that you have the logic of the game complete, let's communicate the **accuracy of the user's input**. Words per Minute (WPM) means nothing without accuracy!

{{< code-action>}} **In `helpers.py` complete the function `calculate_accuracy()` to calculate user's typing accuracy.**  Typing accuracy is calculated by dividing the correct characters typed in by the total total characters typed. For example, if you typed 9 out of 10 characters correctly, you would have .90 accuracy or 90% accuracy.
- parameters: `chosen_prompt`, `user_typed_prompt`
- return value: `accuracy` rounded to decimal place

💭 Be sure to consider the following:

- how do you loop through each letter of the `user_typed_prompt` and compare it to the `chosen_prompt`?
- how do you keep track of correct characters? 
- how do you find the total number of characters? 
- what if the user presses `enter/return` before the end of the prompt?


{{< code-action>}} **Integrate `calculate_accuracy()` into `typing_game.py` so it reports both the `wpm` and `accuracy` to the user.** You should print the user's accuracy as a percentage after the WPM. Consider, how will you convert a decimal to a percentage? 
```shell
WPM: 80.5
Accuracy: 92.2%
```

---

## [2] Deliverables

{{< deliverables  >}}

**Once you've successfully completed the game be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSd9wdOTzOoMhDCXzpjZCJcpDAfB53SeHs_fNQ5ddpuIGDPoog/viewform?usp=publish-editor)**.


{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
  > `-A` adds all changed files
- git status
- git commit -m "describe your drawing and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}

---


## [3] Extensions

{{< look-action >}} **Choose from any of the extension activities below.** Be sure to push to Github any work you do on either of the extensions. 

---

### Adjusted WPM

[Adjusted Words Per Minute](https://support.sunburst.com/hc/en-us/articles/229335208-Type-to-Learn-How-are-Words-Per-Minute-and-Accuracy-Calculated-) is the typing speed adjust for the user's accuracy. It is calculated by `WPM*Accuracy`. For example:
```
wpm = 50.4
accuracy = 80.3%
adjusted_wpm = 40.5
```

{{< code-action >}} **Calculate the user's `adjusted_wpm` and print it to the user.**
```shell
WPM: 80.5
Accuracy: 92.2%
Adjusted WPM: 74.2
```

---

### Generate random prompts

Typing games often increase the difficulty by having the prompts be random words that do not tell a story. For example the prompt may be something like, "score wear question continue friend". It is up to you to write a function that does just that.

{{< code-action >}} **In `helpers.py`, finish the function `generate_prompt()`.**

0. It should **return a string with a prompt** of a random length between 10-15. 
0. It should get the words from the `common_word_list` in `prompts.py`. 

{{< code-action >}} **Integrate `generate_prompt()` into `typing_game.py`.**

---

### Difficulty levels

As you may have noticed, the prompts are quite simple. There is no punctuation, hardly any capital letters, no numbers, or special symbols. It is up to you to create an easy, medium, and hard difficulty level of the game. 

{{< code-action >}} **In `prompts.py`, fill in the `prompt_dictionary` with differing prompts for `easy`, `medium,` and `hard`.** You may get the prompts from online, just be sure to cite your sources in the comments of the file.

{{< code-action >}} **Integrate the difficulty levels into `typing_game.py`.**

- the user should be able to choose which difficulty they want
- based on that difficulty level, the game should pick a random prompt from that difficulty level.