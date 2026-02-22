---
Title: Project Arcade
draft: true
---

# Unit 02 Games Arcade Project

📖 You can find the offical Python Aracde documentation [HERE](https://api.arcade.academy/en/latest/get_started.html).

{{< figure src="images/courses/cs9/unit02/arcade08.png" width="75%" >}}

---

## [0] Planning Booklet 

This is a big project with a lot of room for customization. You will need to:
- outline the type of game you'd like to make
- sketch the map 
- sketch the sprites 
- plan an additional feature(s)

It is important for you to plan the game prior to coding. This will help you stay on track and enable the teachers to provide better help. 

{{< write-action "Plan your game prior to coding in your Team Booklet" >}} 

{{< aside "A few feature ideas" >}}

- player health
- attacking enemies 
- multiple players 
- multiple levels 
- timed level(s)

{{< /aside >}}

---


##  [1] Set Up

{{< code-action "Start by going into your" >}} `cs9/unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/cs9/unit02_games
```

{{< code-action "Clone your starter code." >}} Be sure to change `yourgroupname` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/project_games_arcade_yourgroupname
```

{{< code-action "Enter the Poetry shell and install the requirements:" >}}
```shell
poetry shell
poetry install
```

This repo includes the following files:
- A `project-games-arcade` repository will include all the following files + any additional files:
    - `game.py` 
    - `/assets.py`
        - `/map`
        - `/sprites`
    - `README.md` - a brief description of your game

---

## [2] Deliverables

{{< deliverables  "Projects are due on the last day of class!" >}}

- A `project-games-arcade` repository will include all the following files + any additional files:
    - `game.py` 
    - `/assets.py`
        - `/map`
        - `/sprites`
    - `README.md` - a brief description of your game


---

**🗓️ Timeline**

**You have 4 in class days to complete this project.**

🎉 The last day of class will be a showcase of all of your amazing games! 

---

{{< code-action "Push your work to Github:" >}}
- `git status`
- `git add game.py`
    - you can add all of the changed files with: `git add -A`
- `git status`
- `git commit -m "your message goes here"`
    - be sure to customize this message, do not copy and paste this line
- `git push`
{{< /deliverables >}}

