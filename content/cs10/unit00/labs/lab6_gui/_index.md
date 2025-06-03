---
title: "5. GUI"
type: lab
draft: true
---

# GUI

In this lab we will explore how to create a Grapical User Interface (GUI) for a user to interaction with the Riddle Server. We will use the 
CustomTkinter Library to build our application. 

{{< aside "CustomTkinter Documentation" >}}

📖 View the documentation [HERE](https://customtkinter.tomschimansky.com/documentation/)

{{< /aside >}}

---

## [0] Set Up

We will use the repo from the previous lab, `lab_client`. 

{{< code-action "Go to the lab folder." >}}
```shell
cd ~/desktop/making_with_code/unit03_networking/lab_client_YOURGITHUBUSERNAME
```

{{< code-action "Enter the poetry shell." >}} You do NOT need to install the requirements again. 
```shell
poetry shell
```

📄 **The repository has the following files.**  In this lab we will just focus on the bolded files.
- `riddle_client.py`
- `test_riddle_client.py`
- **`gui_template.py`**
- **`gui_view.py`**

{{< code-action "Open the folder in VS Code:" >}} `code .`


---

## [1] GUI 

If you run `python gui_view.py`, the application does not run. This is becuase the `RiddleGUI` class is defined, but there is no instance of the application. 

{{< code-action >}} **Add the following lines of code to the bottom of `gui_view.py` to create an instance of `RiddleGUI` and call the method `run()`.**

```python
riddle_gui = RiddleGUI()
riddle_gui.run()
```


{{< code-action "Now you may run the python file to launch the application:" >}} `python gui_view.py`. Click on the various buttons to test the interaction

{{< figure src="images/courses/cs10/unit00/06_gui_0.png" width="50%" alt-text="An HTTP GET request"  >}}

{{< aside >}}

You can close the GUI with `command + w`, just like you would a normal window.

{{< /aside >}}


---

### GUI()


**The `GUI()` in `gui_template.py` is the framework for our application using the `CustomTkinter` library.** It has a bunch of properties and
methods that help us set up the application window and widgets.

```python
# gui_view.py 

import customtkinter

class GUI:
    def __init__(self, app_title, width, height):

        self.app = customtkinter.CTk()
        self.app.geometry(f"{width}x{height}")
        self.app.title(app_title)
```



 **It uses CustomTkinter to creates various [widgets](https://customtkinter.tomschimansky.com/documentation/widgets)** 
for the user to interact with and view information, this includes:
- text box widget
- buttons widget
- labels label widget
- entry widget *(input box)*


**`gui_template.py` has a ton of code, you don't have to be too concerned with understanding each line.**
Focus on reading the comments to understand the purpose of each method.  

---

### `RiddlerGUI`

The `RiddlerGUI` in `gui_view.py` is the child class of `GUI()`. It inherits all of the properties and methods from `GUI()`. 

```python
from gui_template import GUI
import customtkinter

class RiddlerGUI(GUI):
    def __init__(self):
        # inherit all the properties and methods from the parent class
        super().__init__(app_title="Riddler",width=800, height=600)

        # create the riddler client object
        self.riddler_client = RiddleClient()
```

👀 **It has the following properties:** 
- `self.riddle_client` - instance of the `RiddleClient` to process the HTTP requests and responses
- `self.menu_dictionary` - stores the menu buttons with the associated method 
- `self.entry_dictionary` - stores the entry widget with its associated placeholder text
- `self.label_dictionary` - stores the labels for the entry widgets with its associated label text
- `self.submit_dictionary` - stores the submit button with the method its associated method
- `self.text_box` - stores the text box widget for displaying the HTTP responses

👀 **It has 2 methods:**
- `view_all_riddles()` 
  - uses `self.riddle_client` to make an HTTP GET request to get all riddles
  - nicely formats each riddle in the text box
- `guess_riddle_submit()` 
  - captures the user entry from the entry widgets
  - uses `self.riddle_client` to make an HTTP POST request
  - nicely formats the response in the text box

--- 

## [2] Extend the GUI


**Your job is to add the ability to `view one riddle` and `add a new riddle` to the `RiddleGUI()`.** 

💻  **Add the ability to `view one riddle` in the `RiddleGUI()`.** What existing code can you reference and modify? 

{{< figure src="images/courses/cs10/unit00/06_gui_2.png" width="75%" alt-text="An HTTP GET request" >}}


{{< expand "Hint" >}}

- add a new menu button 
- add a new submission button
- create a new `view_one_riddle_submit()` method 
- used the `one_riddle()` method from the `RiddleClient()` 
- display the appropriate message in the text box widget 

{{< /expand >}}

💻  **Add the ability to `add a new riddle` in the `RiddleGUI()`.** What existing code can you reference and modify? 

{{< figure src="images/courses/cs10/unit00/06_gui_3.png" width="75%" alt-text="An HTTP GET request" >}}


{{< expand "Hint" >}}

- add a new menu button 
- add a new submission button
- add 2 new entry widgets
- create a new `new_riddle_submit()` method 
- used the `new_riddle()` method from the `RiddleClient()` 
- display the appropriate message in the text box widget 

{{< /expand >}}


---

## [3] Deliverables

{{< deliverables "Once you've successfully completed the client:" >}}  


{{< write-action >}} **Fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLScM7qccLbYlDrzVEWRJKU834Q6VViMmax6ZN8NNybpRpvDJRw/viewform?usp=sf_link)**

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

### Customize the look!

💻 **Explore the [documentation](https://customtkinter.tomschimansky.com/documentation/) and customize the appearnce of your app.**
You may need to edit the `RiddleGUI()` and `GUI()`, depending on which widgets you want to edit.

{{< figure src="images/courses/cs10/unit00/06_gui_4.png" width="75%" alt-text="An HTTP GET request"  >}}

<!-- --

### Gamify!

👾 Currently, the client simply takes care of the HTTP requests in a nicely formatted view. But, **let's make it more fun and turn it into a game!**

{{< code-action "Extend the functionality of the client and allow the user to play a guessing game." >}}

The game should:
- display each riddle on the riddle server
- allow the user to guess each riddle

Gameplay should look something like this:
```shell
-----------------------------------
---- Welcome to the Riddler ----
-----------------------------------

[Riddler Game]
Question: Do you exist?
Enter your guess: no
Correct!

Question: What can fill a room but takes up no space?
Enter your guess: silence
Incorrect!

Question: What cups do not hold water?
Enter your guess:
```

🤔 **Even more extension feature ideas:**
- keep score of how many riddles the user guesses correctly
- display the current score after each riddle is guessed
- randomly display each riddle


--- -->
