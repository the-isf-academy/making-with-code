---
title: "2. Riddler"
type: lab
slug: lab_riddler
repo_url: https://github.com/the-isf-academy/lab-riddler
init_action: clone
# draft: true
---

# Riddler

In this lab we will continue to review classes by making a Trivia game. 



## [0] Setup


{{< code-action "Let's start by cloning the repository" >}} in your `unit03_networking` folder.  Be sure to change `yourgithubusername` to your actual Github username.

```shell
cd ~/desktop/making_with_code/year2_review
git clone https://github.com/the-isf-academy/lab_riddler_yourgithubusername
cd lab_riddler_yourgithubusername
```

{{< code-action "Get the necessary packages:" >}}
```shell
poetry install
```

{{< code-action "Enter the Poetry shell" >}} 
```shell
poetry shell
```
{{< aside "Exiting the poetry shell" >}}
When you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}

📄 **This repository has two files:**
- `riddle.py`: This file has the `Riddle` class
- `riddle_list.py`: This file has a list of `Riddle` instances
- `game.py`: When run, this file should play the riddle guessing game

---

## [1] Riddle Class

Let's start by exploring the `Riddle` class. It has two properties and one method.
```python
class Riddle:
    def __init__(self,prompt,answer):
        self.prompt = prompt
        self.answer = answer


    def check_guess(self,guess):
        #Checks whether a guess is correct.
        #Uses the fuzzywuzzy library to accept guesses which 
        #are close to the answer.

        min_fuzz_ratio = 80
        similarity = fuzz.ratio(guess.lower(), self.answer.lower())

        if similarity >= min_fuzz_ratio:
            return True
        else:
            return False
```
> *To learn more about how `check_guess()` accepts guesses that are very close to the answer, you can visit the [fuzzywuzzy documentation](https://pypi.org/project/fuzzywuzzy/)*

{{< code-action >}} **Open `riddle.py` and look at the bottom of the file.**  We can use this section of the file to run tests on our `Riddle` to ensure it works as expected. 
```python
if __name__ == "__main__":
    r = Riddle(
        prompt = 'What has to be broken before you can use it?', 
        answer = 'an egg')
    
    print(r.prompt)

    # TODO: print the answer
  


    # TODO: call check_guess() and print the return value
```

{{< code-action >}} **Run `riddle.py` to see the output.**
```shell
What has to be broken before you can use it?
```

{{< code-action >}} **Complete the `TODO` items.** Print answer  and use `check_guess()`. Example output should like this this:
```shell
What has to be broken before you can use it?
an egg
False
```


{{< aside "Exiting the python shell" >}}
When you want to exit the shell, you can type `exit()` or `^D`
{{< /aside >}}

{{< code-action >}} **Now that you understand how to create a `Riddle`, open up `riddle_list.py`**

This file contains the list `list_of_riddles` with only one `Riddle()`. 

```python
list_of_riddles = [
    Riddle(
        prompt = 'What has to be broken before you can use it?',
        answer = 'an egg'),    
]
```

{{< code-action  >}} **Add 5 instances of `Riddle()` to `riddle_list`.** [Here](https://www.rd.com/list/easy-riddles/) is a list of riddles, but feel free to write your own!

---



## [2] Creating the Game

Now that you understand how the `Riddle` is structured, it's up to you use it and create a guessing game.

```shell
-----------------------------------
---- Welcome to the Riddler ----
-----------------------------------
```

{{< code-action "Start by opening up" >}} `game.py`

{{< code-action >}} **It is up to you to finish the code in `game.py` to create a riddle guessing game!** The game should:
- loop each `Riddle` in the `list_of_riddles` list
- ask the user to guess the answer
- tell the user if their guess was correct or incorrect


{{< expand "👾 A few helpful functions"  >}}

### User input
```python
name = input('What is your name?')
```

### Looping through a list
```python
animal_list = ['dog', 'cat', 'dragon']
for animal in animal_list:
    print(animal)
```
{{< /expand >}}

🕹️ **Once you've completed your game logic, play test your game!** `python game.py`

```shell
-----------------------------------
---- Welcome to the Riddler ----
-----------------------------------

Riddle 1: What is black and white and read all over?
Guess: newspaper
Correct :)

Riddle 2: What has to be broken before you can use it?
Guess: A chicken
Incorrect :(

```
---

## [3] Deliverables


{{< deliverables "Congrats on completing the lab!" >}}  

Once you've successfully completed the lab, fill out [this Google form](https://forms.gle/HP5Cpp9j4ecrpWVm7).


{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push
{{< /deliverables >}}

---

## [4] Extension: Additional Features

Now that we've got a basic riddle guessing game, let's improve it!

### Simple Improvements

Let's start with a few simple improvements.
- tracking user guesses
- randomizing order of riddles

{{< code-action "Keep track of the user's guesses and provide a score at the end." >}} For example once the user guessed all of the riddles, it may print:
```shell
Score: 3/5
```

{{< code-action "Randomize the order of the riddles." >}} Use the random library to change the order the riddles are given each time the user plays the game.
> *You may want to look at the [Random library documentation](https://docs.python.org/3/library/random.html#module-random) for a hint*


---

### Difficulty Settings

Currently, there are no difficulty settings for the game. Some riddles are easy, some riddles are difficult, and some riddles are in-between.

{{< code-action "Implement a difficulty setting in your game to make it more accesisble." >}} Your game should allow the user between easy, medium, or hard riddles. This will require you to change the `Riddle` class and the game play flow in `game.py`.
> *Hint: what property could you add to store the difficulty of each riddle?* 

---

### Add Terminal Menu System

Although the Riddler is functional, it is not the most exciting looking game. Let's spice it up with colors!


{{< code-action >}} **Explore the package [colorama](https://pypi.org/project/colorama/) to add color to your game!**

> The package is already installed, but you will need to add the import statements to the top of `game.py`.
