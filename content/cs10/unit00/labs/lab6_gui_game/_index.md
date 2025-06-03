---
title: "6. GUI Game"
type: lab
draft: true
---

# GUI Game

In this lab we create a guessing game with a Grapical User Interface (GUI) using the
CustomTkinter Library. 

{{< aside "CustomTkinter Documentation" >}}

📖 View the documentation [HERE](https://customtkinter.tomschimansky.com/documentation/)

{{< /aside >}}

{{< aside "Updates to the server" >}}

🌐 The [riddle server](http://sycs.student.isf.edu.hk/riddle/all) has been updated per requests! 

The JSON now includes the riddle's answer and difficulty score. 
{{< /aside >}}



---

## [0] Set Up


{{< code-action "Go to the unit folder, clone the riddler server lab, and cd into the repo." >}}
```shell
cd ~/desktop/making_with_code/unit03_networking/
git clone https://github.com/the-isf-academy/lab_gui_game_YOURGITHUBUSERNAME
cd lab_gui_game_YOURGITHUBUSERNAME
```

{{< code-action "Install the requirements." >}}
```shell
poetry install
```

{{< code-action "Enter the poetry shell." >}}
```shell
poetry shell
```

📄 **The repository has the following files.**  In this lab we will just focus on the bolded files.
- `riddle_client.py`
- **`gui_template.py`**
- **`gui_view_game.py`**

{{< code-action "Open the folder in VS Code:" >}} `code .`


---

## [1] Play the game! 

**💻 Play the game!** `python gui_view_game.py`.

{{< figure src="images/courses/cs10/unit00/07_gui_1.png" width="75%"  >}}


---

## [2] Improve the Game

**💻 Add the following features to the game**

&nbsp;&nbsp;&nbsp;**[✔️]** randomize the order of the riddles each time

&nbsp;&nbsp;&nbsp;**[✔️]**  add a score feature

&nbsp;&nbsp;&nbsp;**[✔️]** add lives feature (e.g. 3 guesses until game over)

&nbsp;&nbsp;&nbsp;**[✔️]** add game over screen


{{< expand "Hint" >}}

- look into the `shuffle()` function
- what properties will you need to add to track the `score` and `lives`?
- how will you know if the game is over? 

{{< /expand >}}



---

## [3] Deliverables

{{< deliverables "Once you've successfully completed the client:" >}}  


{{< code-action "Push your code to Github." >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}


---

## [4] Extension

### Difficulty Modes

💻 **Add a difficulty feature using [combo box widget](https://customtkinter.tomschimansky.com/documentation/widgets/combobox)** Users should be able to choose between easy, medium, or hard mode. 

{{< figure src="https://python-hub.com/wp-content/uploads/2023/11/Screenshot-2023-11-26-135852.png" width="20%"  >}}


**The API [`/riddle/all`](http://sycs.student.isf.edu.hk/riddle/all) has been updated to include difficulty score.**
- `1.0` represents a riddle with 0% correct guesses 
- `0.5` represents a riddle with 50% correct guesses
- `0.0` represents a score with 100% correct guesses

```shell
{
"riddles": [
  {
    "id": 1,
    "question": "I’m light as a feather, yet the strongest person can’t hold me for five minutes. What am I?",
    "answer": "Your breath",
    "difficulty": 0.9885931558935361,
    "correct": 2,
    "guesses": 262
  },
]
```

{{< expand "Hint: Creating a Combobox" >}}

To create a combobox:

```python
combobox = customtkinter.CTkComboBox(
    app, 
    values=["option 1", "option 2"]
    )
```

To access the selected value:

```python
combobox.get()
```
{{< /expand >}}


---

### A progress bar

💻 **Add a [progress bar widget](https://customtkinter.tomschimansky.com/documentation/widgets/progressbar) to communicate to the user their progress in the game.**

{{< figure src="https://python-hub.com/wp-content/uploads/2023/12/CTkProgressBar.png" width="25%"  >}}

<!-- ---


### A local leaderboard

💻 **Add a high score leaderboard feature.** You will need to learn how to [read and write to a file](https://www.geeksforgeeks.org/reading-writing-text-files-python/).
- Due to the lack of  -->