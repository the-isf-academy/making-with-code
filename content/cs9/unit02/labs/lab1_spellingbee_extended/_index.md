---
title: 2. Spelling Bee [extended]
draft: true
---

# Spelling Bee

In this lab, you will learn about the different layers that make up a game.

---

## [0] Play the Game


👾 **Let's start by playing Spelling Bee: [https://www.nytimes.com/puzzles/spelling-bee](https://www.nytimes.com/puzzles/spelling-bee).**

{{< checkpoint >}}

✏️ **As you play, complete the worksheet with your partner.** 

Consider, how would you build this game in Python?

{{< /checkpoint >}}

---

## [1] Setup

{{< code-action "Start by going into your" >}} `unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/unit02_games
```

{{< code-action "Clone your starter code." >}} Be sure to change `YOUR-GITHUB-USERNAME` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab_spellingbee_extended_YOUR-GITHUB-USERNAME
```

{{< code-action "cd into the lab" >}}
```shell
cd lab_spellingbee_extended_YOUR-GITHUB-USERNAME
```

{{< code-action "Enter the Poetry shell and install the requirements:" >}}
```shell
poetry shell
poetry install
```


This lab includes the following files to play the Spelling Bee game:
- `model.py`
- `game.py`
- `view.py`
- `wordslist.py`
- `helpers.py`


In this version of Spelling Bee, the game is separated into 3 distinct layers:
- game structure (`model.py`)
- game logic (`game.py`)
- game output (`view.py`)

{{< figure src="images/courses/cs9/unit02/01_spellingbee.png" width="100%" >}}


---

## [2] Implementing the Model 


{{<mermaid align="left">}}
classDiagram
    class SpellingBee {
        + word_list: [] str
        + letter_list: [] str
        + keyletter: str
        + guessed_words: [] str
        + check_guess(user_guess) boolean
        + check_keyletter(user_guess) boolean
        + check_length(user_guess) boolean
        + check_letters(user_guess) boolean
        + check_already_guessed(user_guess) boolean
    }
{{< /mermaid >}}

This a **UML Diagram** (Unnified Modeling Language) of the `SpellingBee` class. 
- `row 1` - the class name
- `row 2` - the attributes with the data type 
- `row 3` - the methods with the parameter and return data type

> Remember, an `attribute` is a variable associated with a class and a `method` is a function associated with a class


{{< code-action >}} **Open the file `model.py` and finish `methods` in the `SpellingBee` class by referencing the UML diagram.** 

{{< code-action >}}  **Test your code at the bottom of the file in the `if __name == "__main__":` section and run `python model.py`.** This section is only called when file is ran, not when the file is imported.

```python
if __name__ == "__main__":
    
    spelling_bee = SpellingBee(
        word_list = ["hat","cat"],
        letter_list = ["h","a","t", "c"],
        keyletter= "a"
    ) 

    # testing check_keyletter()
    print(spelling_bee.check_keyletter("rat"))
    print(spelling_bee.check_keyletter("rot"))
```

---

### Using the `in` Keyword

{{< look-action >}} **The keyword `in` can be very useful when working with strings:**

#### 🔁 Looping

```python
word = "cobra"
for letter in word:
    print(letter)
```

#### 🔎 Checking for sub-strings using `in`

```python
word = "cobra"
if "a" in word:
    print("Here!")
```

```python
word = "cobra"
if "z" not in word:
    print("Not here!")
```

---

## [3] Implementing the view and the game logic

**Begin by running the game. 🤔 It works perfectly, but is incomplete!**

```shell 
---Welcome to Spelling Bee---

[RULES]
You can use any of these letters: ['T', 'C', 'O', 'L', 'I', 'N', 'M']
You must you use the letter M
Guesses must be more than 3 letters long

---Enter word:---
 > mint

  -correct!-  
```

{{< code-action >}} **Open the file `game.py` and `view.py` and complete the game logic.** You will need to use the `SpellingBee` methods and the `TerminalView` methods. 
- ensure the game works like the actual game
- only write `print()` statements in the `TerminalView` methods. Why do you think this is?


{{< code-action "Test your game after every change with" >}} 

```shell
python game.py
```

---

## [4] Deliverables

{{< deliverables  >}}

**Once you've successfully completed the game be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSczCgC8Y3nJeqDh30MVe7O-WXqEkoL17fc00ZBWQw-djTwcig/viewform?usp=sf_link)**.


{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your game and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}


---


## [5] Extensions 

Choose one of the extensions below to improve your game!


### Score

**In the original Spelling Bee, you get points when you guess correct words.** To make this work, we will have to make changes in each of our three main files: `models.py`, `game.py`, and `view.py`.

{{< code-action >}} **In `model.py`, implement a score feature in the `SpellingBee()` class.** You will need to:
- create an attribute
- update a method

> How can you test if it worked?

{{< code-action >}} **Now, incorporate the score into `view.py`. Write a new method `score()` to print out the user's score.** It should take the parameter `current_score`. 
- which file should you call this method?

👾 **Test our your game to see how the new feature works!** 

---

### Advanced Scoring

In the original Spelling Bee game, you get more points for longer words. 

{{< code-action >}} **Change your `correct_word` method so that it gives more points for higher words** 

---

### Randomized Congratulations

In the original Spelling Bee game, they give you a variety of different messages when you get a correct word, such as "Nice!", "Good work!", etc. 

{{< code-action >}} **Randomize which message the user receives when they get a word correct** 

You will need to use  `choice` from the `Random` library.

Add this to the top of your code:
```python
from random import choice
```

Here is an example of how to use choice:
```python
from random import choice

mylist = ["apple", "banana", "cherry"]
random_fruit = choice(mylist)
```
You can reference your auto-poetry lab from the data science unit for inspiration!

---

### Menu

Currently, this game does not have a menu system. **It's up to you to implement one!**

{{< code-action >}} **Implement the `menu` from `helpers.py` into `game.py`.** A user should be able to:

- make a guess
- view the rules 
- view their previous successful guesses
- quit the game

---


### File I/O


{{< code-action "Keep a high score using a simple text file to save and update the score." >}} Learn [file handling here](https://www.w3schools.com/python/python_file_handling.asp
).




