---
Title: Project Pyxel
draft: True
---

# Unit 02 Games: Pyxel Project

UPDATE PAGE FOR PYXEL

🎨 **Design Prompt:** You will create a maze game or a platforming game. You must include at least one new, unique mechanic.



INCLUDE PICTURE

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
- power up items
- enemies 
- multiple levels
- shooting
- multiplayer 

Some dynamics to cosnider focusing on. IT cna help to focus on a dynamic and then brainstorm mechanics to fit that dynamic. 


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
- UPDATE

---
## [2] Assessment




✅  **This project will be assessed on the following criteria:**
- **Planning** 
    - I can consider the aesthetics of my game
    - I can consider a new mechanic for my game 
    - I can create a UML diagrams and consider how the methods will work 
- **Iterative Development**
    - I can track the development of my project by successfully committing to Github a minimum of each class work day, preferably after each work session
    - I can write descriptive commit messages that accurately describe the changes made
    - I can systematically break down my project into smaller chunks  
- **Aesthetic Implementations**
    - I can use the Pyxel Editor to create a custom tileset that includes an array of sprites that matches my planning document
    - I can implement my tileset into my game so each sprite works as expected 
- **Mechanic Implementation**
    - I can create a new class or build upon on existing class to add a new mechanic 
    - I can test my game thoroughly to ensure the mechanic works as planned
- **Readability**
    - I can use descriptive names for modules, variables, classes, and methods
    - I can write descriptive comments to describe complex pieces of the code 

**For each criteria you will be assessed on a score from 0-3. With 5 criteria, there is a total of 15 potential points.** 
- 0 - no evidence of the practice
- 1 - limited evidence of the practice
- 2 - satisfactory evidence of the practice
- 3 - substantial evidence of the practice


---

## [3] Deliverables


{{< deliverables  "" >}}

- A `Unit 02 Games Project: Planning Document` 
- A `project_game_story` repository will include some if not all the following files:
    - UPDATE!!! 
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

ADD TIPS FOR PYXEL & LOOKING AT TILESETS


### 👾 Games for inspiration

REPLCAE WITH GAMES 

---

###  ⏱ Time
If you are interested in including an element of time in your game (a countdown, a stopwatch, etc.), follow along with these steps. You can also reference `lab_typing_game` which used the `time()` to calculate wpm.

**Be sure to import the time library and any functions you want to use at the top of the file.** 

**`time()`**  - *save the current time into a variable*
```python
from time import time

#save the current time
current_time = time()

end_time = time()

elapsed_time = end_time - current_time

```

