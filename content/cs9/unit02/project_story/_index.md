---
Title: Project Story
draft: True
---

# Unit 02 Games: Story Project

🎨 **Design Prompt:** You will create a text-based game inspired by a real piece of media or your own life. 

{{< code-action >}} **Your game must include one unique feature.** For example:


It is totally up to you what type of story you make. For example you could make:
- choose your own adventure game 
- exploration game
- puzzle game 
- narrative story game



{{< figure src="https://steamuserimages-a.akamaihd.net/ugc/1791848543425884907/18A8A93A2B7215E654F50350F4C896FFE463B456/" width="70%" >}}
> [*Zork*](https://en.wikipedia.org/wiki/Zork) is often noted as one of the best video games of all time. 
>
>*"What Zork seemed to contribute more than anything was the idea that the computer could simulate a rich virtual environment" - [Matt Barton](https://web.archive.org/web/20220809014122/https://www.gamedeveloper.com/pc/the-history-of-zork)*



---

## [0] Planning Document

This is a big project with a lot of room for customization. It is important for you to plan the game prior to coding. 

**✏️ Plan your game in the Canva document:**  [`Unit 02: Games Project Planning Document `](https://www.canva.com/design/DAGizT2u_b4/vwyZ9k9cH6NviN_L7UUGxQ/edit?utm_content=DAGizT2u_b4&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)
- Open the Link
- File > Make a Coopy
- Share with teacher 
- Change name of file to include name

1️⃣ outline your game overview <br>
2️⃣ outline your feature <br>
3️⃣ outline the feature implementation in the logic of the game<br>
4️⃣ outline the story in a graph diagram 

🧠 Some idea for features:
- branches that come back together into the same Node
- ability to go back to a previous node
- some nodes send you back to the beginning
- time limit - user must make a choice quickly, OR ELSE
- auding audio or images to nodes
- variable messaging in the story associated with user actions
    - *e.g. "you have visited this store 5 times"*
- a Player() class with unique properties
    - *e.g. hunger, money, or health*
- adding enemies to the game
- certain nodes or parts of the story give you items
    - *e.g. a locked door where you need to first collect the key in a certain room.*

---


##  [1] Set Up

{{< code-action "Start by going into your" >}} `unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/unit02_games
```

{{< code-action "Clone your starter code." >}} Be sure to change `yourgithubusername` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/project_game_story_yourgithubusername
```
```shell
cd project_game_story_yourgithubusername
```

{{< code-action "Enter the Poetry shell and install the requirements:" >}}
```shell
poetry shell
poetry install
```

This repo includes the following files:
- `game.py` - when this program runs, it should launch your game
- `view.py`
- `story_setup.py`
- `model_story.py`
- `model_node.py`
- `README.md` - a brief description of your game


---
## [2] Assessment


✅  **This project will be assessed on the following criteria:**
- **Planning [3]** 
    - I can consider the components of my game before coding
    - I can create a UML diagram my feature with appropriate data types
    - I can consider how to implement the feature into the game logic
    - I can create a graph diagram to outline the branches of my story
- **Iterative Development [3]**
    - I can track the development of my project by successfully committing to Github a minimum of each class work day, preferably after each work session
    - I can write descriptive commit messages that accurately describe the changes made
    - I can systematically break down my project into smaller chunks  
- **Feature Implementation [3]**
    - I can design and implement the necessary class(es) with appropriate properties and methods to fully realize my feature(s).
    - I can write a feature that is well abstracted
        - can be used in multiple scenarios within the game  
        - can be extended or adapted by another developer or student
    - I can use descriptive names for modules, variables, classes, and methods to enhance code readability
    - I can write descriptive comments to describe complex pieces of the code
- **Game Implementation [3]**
    - I can test the game thoroughly to ensure the user interface behaves as expected and matches the Game Logic Flowchart
    - I can implement a full functioning version of my graph diagram, ensuring all planned Nodes and connections are accurately represented
    - I can design a `View` that is easily to read and understand
    - I can use descriptive names for modules, variables, classes, and methods
    - I can write descriptive comments to describe complex pieces of the code 


<!-- **For each criteria you will be assessed on a score from 0-3. With 5 criteria, there is a total of 15 potential points.** 
- 0 - no evidence of the practice
- 1 - limited evidence of the practice
- 2 - adequate evidence of the practice
- 3 - substantial evidence of the practice

{{< expand "Scoring Breakdown" >}}

The project is scored out of 15. 

*To calculate your score for the practices & concepts, look at the following bands:*

- 1 = 0
- 2 = 1
- 3 = 2-3
- 4 = 4-6
- 5 = 7-11
- 6 = 12-13
- 7 = 14-15
{{< /expand >}} -->


---

## [3] Deliverables

<!-- Projects are due during Week 31-32. -->

{{< deliverables  "" >}}

- A `Unit 02 Games Project: Planning Document` 
- A `project_game_story` repository will include some if not all the following files:
    - `game.py` 
    - `view.py`
    - `story_setup.py`
    - `model_story.py`
    - `model_node.py`
    - `README.md` - a brief description of your game
<!-- 
---
**🗓️ Timeline**

**You have 5 in class days to complete this project.**


| CS9.1 Dates  | CS9.2 Dates  | Agenda                           |
|--------------|--------------|----------------------------------|
| 19 Apr       | 17 Apr       | Project Intro & Planning Booklet |
| 24 Apr       | 22 Apr       | Work Day                         |
| 25 Apr       | 23 Apr       | Work Day                         |
| 26 Apr       | 25 Apr       | Work Day                         |
| 30 Apr       | 29 Apr       | Due at End of Class              | -->

---

{{< code-action "Push your work to Github:" >}}
- `git status`
- `git add -A`
- `git status`
- `git commit -m "your message goes here"`
    - be sure to customize this message, do not copy and paste this line
- `git push`
{{< /deliverables >}}

---

## [4] Resources

### 👾 Games for inspiration
**If you need inspiration, explore these narrative games.** As you play, consider the different genres and what's possible with this structure. 
- [Harry Potter - Sorting Hat](https://unfold.studio/stories/303/)
- [Oregon Trail 1971](https://unfold.studio/stories/10782/)
- [City Exploration](https://unfold.studio/stories/2649/)
- [Store front Example, variables](https://unfold.studio/stories/1065/)

---
<!-- 
### ✏️ AI tools
If you need help writing the text, feel free to use an AI service. Just be sure to cite your transcript in the Planning Doc.
- [poe](https://poe.com/)
- [rytr](https://rytr.me/)
- [composeai](https://www.compose.ai/#:~:text=Compose%20AI%20is%20a%20free,some%20of%20our%20personalization%20features.) -->

---

### 👀 Readability
Here are a few resources that may help improve readability.
- [Emojis](https://www.emojicopy.com/)
- [InquirerPy](https://inquirerpy.readthedocs.io/en/latest/)
    - This is the package that controls the menu
- [Colorama](https://pypi.org/project/colorama/)
    - This package adds colors to the print statements in the Terminal

---

###  🔉 Play Sound
If you are interested in including sounds in your game, follow along with these steps.

(0) **Install the playsound library:** `pip3 install playsound`

(1) **Add a sound file to your repository.** *e.g. .mp3, .m4a, .wav file.*
> If will have multiple sounds, be sure to consider how you will organize your repostiory.

(2) **Incorporate the sound into your game.** If this is your feature, I highly planning how you will incorporate this into the `Node()`, `Story()` and/or `game.py`.

```python
from playsound import playsound

playsound('test_sound.m4a')
```

---

### 🌄 Open Images

If you are interested in including images in your game, follow along with these steps. It will open the image in your computer's default image viewer *(e.g. Preview)*.

(0) **Install the playsound library:** `poetry add pillow`

(1) **Add a image file to your repository.** *e.g. .png, .jpg file*
> If will have multiple images, be sure to consider how you will organize your repository.

(2) **Incorporate the image into your game.** If this is your feature, I highly planning how you will incorporate this into the `Node()`, `Story()` and/or `game.py`.


```python
from PIL import Image

image1 = Image.open(r"test_img.png") 
image1.show()
```

---

###  ⏱ Time
If you are interested in including an element of time in your game (a countdown, a stopwatch, etc.), follow along with these steps. You can also reference `lab_typing_game` which used the `time()` to calculate wpm.

**Be sure to import the time library and any functions you want to use at the top of the file.** 

**`time()`**  - *save the current time into a variable*
```python
from time import time

#save the current time
current_time = time()
```

**`sleep()`** - *pause your program for a given amount of seconds.*
```python
from time import sleep

#pause program for 3 seconds
sleep(3)
```

---

### 🌄 ASCII Art

ASCII Art is low-fi art that will print directly in the Terminal. For example...

```
 |\    o
    |  \    o
|\ /    .\ o
| |       (
|/ \     /
    |  /
     |/
```

💻 **The code for this looks like:**
```python
print("""\
     |\    o
    |  \    o
|\ /    .\ o
| |       (
|/ \     /
    |  /
     |/
""")
```
> *Note the `"""\` at the start and the `"""` and the end of the print statement*

🌐 **Here are a few links to find and create your own ascii art.** Just be sure to site what you use in your `README.md`
- [asciiart.eu/](https://www.asciiart.eu/)
- [ascii art text](https://patorjk.com/software/taag/#p=display&f=Epic&t=Hello)