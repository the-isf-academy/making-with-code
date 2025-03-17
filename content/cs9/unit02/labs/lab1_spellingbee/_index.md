---
title: 2. Spelling Bee
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
git clone https://github.com/the-isf-academy/lab_spellingbee_YOUR-GITHUB-USERNAME
```

{{< code-action "cd into the lab" >}}
```shell
cd lab_spellingbee_YOUR-GITHUB-USERNAME
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

---

## [2] Fixing the View 

In this version of Spelling Bee, the game is separated into 3 distinct layers:
- game structure (`model.py`)
- game logic (`game.py`)
- game output (`view.py`)

{{< figure src="images/courses/cs9/unit02/01_spellingbee.png" width="100%" >}}

Most of the game structure and the game logic are complete. **You will start by customizing the game output.**

---

### Play the Game

**We'll begin by running the game. 🤔 It works perfectly, but the messages are confusing!**

```shell 
---Welcome to Spelling Bee---

[RULES]
You can use any of these letters: ['T', 'C', 'O', 'L', 'I', 'N', 'M']
You must you use the letter M
Guesses must be more than 3 letters long

---mystery message 0---
 > lion

  -mystery message 3-  

---mystery message 0---
 > mom

  -mystery message 1-
```


{{< code-action "Start by playing the game." >}} 

```shell
python game.py
```

---

### Solving the Mysteries

**In `view.py`, we have the `TerminalView` class, which is purely responsible for input and output to the user.** In this case, it gets the guess from the user and gives them messages. It does not affect the game flow or logic. 

Right now, the error messages aren't helpful:

```python
    def too_short(self):
        print("\n  -mystery message 1-  ")
```

{{< code-action >}} **Edit each method in the `TerminalView()` class so that the messages are more clear for the user.** 

{{< code-action >}} **Play test your game to make sure it works bug free!** 

```shell
python game.py
```

👾 **Swap with your partner, and see how they implemented their `TerminalView()`!** 

---

## [3] Duplicate Guesses

**Right now, the user doesn't get an error message if they guess the same word multiple times.** 

```shell
---Guess a word!---
 > limit

  Great job, thats correct!  

---Guess a word!---
 > limit

  Great job, thats correct! 
```

**We are already keeping track of all their correct guesses in a list called `guessed_words`. This is a property of the SpellingBee class in `model.py`**

```python {linenos=table, hl_lines=["8"],linenostart=1}
class SpellingBee:
    def __init__(self, word_list, letter_list, keyletter):
        # initializes a spelling bee object with it's properties

        self.word_list = word_list
        self.letter_list = letter_list
        self.keyletter = keyletter
        self.guessed_words = []
```

**Every time they make a correct guess, their guess is added to this list**

```python {linenos=table, hl_lines=["3"],linenostart=28}
    def correct_word(self, word):
        # adds the correct word to the list of guessed words
        self.guessed_words.append(word)
```
We can use the `guessed_words` list to check whether a word is a repeat or not, and then give them the correct error message. To make this work, we will have to make changes in each of our three main files: `models.py`, `game.py`, and `view.py`.

---

### Changing the Model
{{< code-action >}} **In `model.py`, add a new method to the `SpellingBee` class called `check_if_repeat()`. It should check whether a certain word is a repeated guess. It will return True if it's a repeat or False if it's new.** 

Hint: it will be very similar to the method `check_wordlist()`:

```python
    def check_wordlist(self, user_guess):
        # checks whether the user's guess is a real word or not
        # returns true or false

        if user_guess in self.word_list:
            return True
        else:
            return False
```

---

### Changing the View
{{< code-action >}} **In `view.py`, add a new method to the `TerminalView` class called `repeat_guess()`. It should print out an error message letting them know they've guessed that word before.** 

---


### Changing the Game

**Now that we've changed both the `model` and the `view`, it's time to put the pieces together!

{{< code-action >}} **In `game.py`, add a new elif statement that checks whether the user has guessed this word already, and then gives them the correct error message.** Make sure you're using the two methods you just created in your `model` and `view`!


{{< aside >}}
**Remember, to call a method you need to specify which object you're calling it on:**

❌ `check_if_repeat(user_guess)`

✅  **`spelling_bee.`**`check_if_repeat(user_guess)`
{{< /aside >}}

---


## [4] Score 

**In the original Spelling Bee, you get points when you guess correct words.** To make this work, we will have to make changes in each of our three main files: `models.py`, `game.py`, and `view.py`.

---

### Changing the Model

**First, we need to be able to keep track of the user's score. For this we will use a property.** SpellingBee already has 4 properties:

```python  {linenos=table, hl_lines=["5", "6", "7", "8"],linenostart=1}
class SpellingBee:
    def __init__(self, word_list, letter_list, keyletter):
        # initializes a spelling bee object with it's properties

        self.word_list = word_list
        self.letter_list = letter_list
        self.keyletter = keyletter
        self.guessed_words = []
```

{{< code-action >}} **In `model.py`, add a new property called `score` into the `SpellingBee()` class.** What do you think a good starting value is for the user's score?

---

Now that we have a property to store the score, we need to make sure we increase it at the correct times. **We only want to increase the score when someone guesses a correct word.**

Remember the `correct_word()` method? It is called whenever someone guesses a correct word. 

```python {linenos=table, linenostart=28}
    def correct_word(self, word):
        # adds the correct word to the list of guessed words
        self.guessed_words.append(word)
```

We can add to this method so that it also updates the score. 


{{< code-action >}} **Add a line of code to the method `correct_word()` so that it increases the user's score by 1.** 

---
**Now it's time to test if your changes worked!**

{{< code-action >}} **In `game.py` add a print statement that prints out the score.**

```python
print(spelling_bee.score) #prints out the current score
```

{{< code-action >}} **Now try running your game. Does the score increase as you expect?**

***After you've tested and it works, you can delete this print statement***

---

### Changing the View
**When the user guesses correctly, we should let them know what their score is!** We can't just print it out in `game.py`, because we want to ***keep all our user messages in the `TerminalView` class***. However, the `TerminalView` class doesn't know what the score currently is. We need to pass that information using a parameter.

{{< code-action >}} **In `view.py` change the method `correct()` so that it expects a parameter called `current_score`. Then you can use this parameter to print out the user's score as part of their success message!** Remember, a parameter goes in the brackets. 

Here is an example of two parameters, `name` and `age`, being used in a string:
```python
  def introduce(self, name, age):
      print(f"Her name is {name}, and she is {age} years old")
```

---

**Now that you added the `current_score` parameter, whenever you use the `correct()` method, you will need to include the current score in the brackets.** For example, this is how we would use the introduce method from the example above:

```python
terminal_view.introduce(my_pet.name, my_pet.age)
```

{{< code-action >}} **In `game.py`, change the call to the `correct()` method to include the `score` parameter.** Remember that the score is a property of your `spelling_bee` object.

---

👾 **Test our your game to see how the new feature works!** 

---


## [5] Deliverables

{{< deliverables  >}}

**Once you've successfully completed the game be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSczCgC8Y3nJeqDh30MVe7O-WXqEkoL17fc00ZBWQw-djTwcig/viewform?usp=sf_link)**.


{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your drawing and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}


---

## [6] Extensions

Choose one of the extensions below to improve your game!

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

> *Hint: take a look at the `game_interface.py` and `helpers.py`the Pet lab. What will you need to copy?*

---

### Multiple difficulty levels

Every time you play the game, it's exactly the same. 

{{< code-action >}} **Incorporate at least 2 `SpellingBee()` objects that the user can choose from.** 







