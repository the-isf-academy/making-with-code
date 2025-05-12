---
title: 5. Arcade Examples
draft: True
---

# Python Aracde Intro Lab

In this lab you explore the Python Aracde framework through example games.

{{< figure src="https://api.arcade.academy/en/latest/_images/arcade-logo.svg" width="20%" >}}


📖 You can find the offical documentation [HERE](https://api.arcade.academy/en/latest/get_started.html).

--- 

## [0] Setup

You will be running a game from your terminal, so your terminal will need permission to monitor your input.

{{< code-action >}} **Go to Settings > Security &  Privacy > Privacy. Scroll to Input Monitoring and add Terminal.** Terminal to need to restart in order to save this preference.

{{< figure src="images/courses/cs9/unit02/02_02_input_monitoring_permission.png" width="400px" >}}


{{< code-action "Start by going into your" >}} `cs9/unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/unit02_games
```

{{< code-action "Clone the repo." >}}  Be sure to change `YOUR-GITHUB-USERNAME` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab_arcade_intro_YOUR-GITHUB-USERNAME
```

{{< code-action "cd into the lab" >}} 
```shell
cd lab_arcade_intro_YOUR-GITHUB-USERNAME
```

{{< code-action "Enter the Poetry shell and install the requirements:" >}}
```shell
poetry shell
poetry install
```

This repo includes the following files:
- `game1.py`
- `game2.py` 


---


## [1] Explore the Games

👾✏️ **Explore the games, and follow along with the worksheet!** You can use the arrow keys to move around the level.


```shell
python game1.py 
```
{{< figure src="images/courses/cs9/unit02/arcade00.png" width="400px" >}}



```shell
python game2.py
```
{{< figure src="images/courses/cs9/unit02/arcade01.png" width="400px" >}}


---


## [2] Deliverables


{{< deliverables  >}}


{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your drawing and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push


{{< /deliverables >}}