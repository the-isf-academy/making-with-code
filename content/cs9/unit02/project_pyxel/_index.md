---
Title: Project Pyxel
draft: True
---

# Unit 02 Games: Pyxel Project

UPDATE PAGE FOR PYXEL

🎨 **Design Prompt:** You will create a maze game or a platforming game. You must include at least one new, unique mechanic.

{{< figure src="![images/courses/cs9/unit02/pyxel6.png](https://private-user-images.githubusercontent.com/678802/421119679-9cc84780-1e72-4484-b71b-ee8669cb8904.gif?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzMxMTQxNzEsIm5iZiI6MTc3MzExMzg3MSwicGF0aCI6Ii82Nzg4MDIvNDIxMTE5Njc5LTljYzg0NzgwLTFlNzItNDQ4NC1iNzFiLWVlODY2OWNiODkwNC5naWY_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwMzEwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDMxMFQwMzM3NTFaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT02ZmFkYjgzM2RhZWFmZDFjZjk4ZWUzNGY5ZjljMjRmODc1NGUwZDhlNDllNGVmNThmY2VjNDZlNTJiNzhkNGJiJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.1St9yONqqsPW4mlLufXM8RgfoPNvj4VtvoE9iR5129U)" width="50%" >}}



---

## [0] Planning Document

This is a big project with a lot of room for customization. It is important for you to plan the game prior to coding. 

**✏️ Plan your game on the planning document:**  `Unit 02: Games Project Planning Document`


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



---


##  [1] Set Up

{{< code-action "Start by going into your" >}} `unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/unit02_games
```

{{< code-action "Clone your starter code." >}} Be sure to change `GROUPNAME` to your group name.
```shell
git clone https://github.com/the-isf-academy/project_pyxel_GROUPNAME
```
```shell
cd project_pyxel_GROUPNAME
```

{{< code-action "Enter the Poetry shell and install the requirements:" >}}
```shell
poetry shell
poetry install
```

This repo includes the following files:
- assets.pyxres
- coin.py
- game.py
- helpers.py
- player.py

---
## [2] Assessment


✅  **This project will be assessed on the following criteria:**
- **Planning** 
    - I can define a specific aesthetic for my game and explain how my art choices support it
    - I can describe a new game mechanic and outline the logic needed to implement it
    - I can design sprites and a map layout  
    - I can create UML diagrams that accurately plan the attributes and methods 
- **Iterative Development**
    - I can track the development of my project by successfully committing to Github a minimum of each class work day, preferably after each work session
    - I can write descriptive commit messages that accurately describe the changes made
    - I can systematically break down my project into smaller chunks  
- **Aesthetic Implementations**
    - I can use the Pyxel Editor to draw custom tiles and sprites that match the designs in my planning doc
    - I can implement a functional map where walls, floors, and sprites are placed correctly according to my sketch.
- **Mechanic Implementation**
    - I can extend the game’s functionality by adding a new class or building on an existing class
    - I can develop a new mechanic so that it works as planned during gameplay
    - I can test my game thoroughly to ensure the mechanic works in different scenarios
- **Readability**
    - I can use descriptive names for modules, classes, attributes, and methods f
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
- A `project_pyxel_GROUPNAME` repository will include some if not all the following files:
    - assets.pyxres
    - coin.py
    - game.py
    - helpers.py
    - player.py
    - any other files you created
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

