---
title: 6. Pyxel Map
draft: True
---

# Pyxel Map Lab

In this lab you explore the Python Pyxel map editing tool. 

{{< figure src="https://pypi-camo.freetls.fastly.net/4719e8485b21bcca6daab788e107399cf54ab216/68747470733a2f2f7261772e67697468756275736572636f6e74656e742e636f6d2f6b6974616f2f707978656c2f6d61696e2f2f646f63732f696d616765732f696d6167655f74696c656d61705f656469746f722e676966" width="50%" >}}


📖 **You can find the official documentation [HERE](https://github.com/kitao/pyxel).**

--- 

## [0] Setup


{{< code-action "Start by going into your" >}} `unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/unit02_games
```

{{< code-action "Clone the repo." >}}  Be sure to change `YOUR-GITHUB-USERNAME` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab_pyxel_map_YOUR-GITHUB-USERNAME
```

{{< code-action "cd into the lab" >}} 
```shell
cd lab_pyxel_map_YOUR-GITHUB-USERNAME
```



{{< code-action "Enter the Poetry shell and install the requirements:" >}}
```shell
poetry shell
poetry install
```

{{< expand "If issues with install..." >}}
```shell
brew install pipx
pipx ensurepath
pipx install pyxel
```
{{< /expand >}}

This repo includes these key files:
- `game.py`
- `player.py`
- `coin.py`
- `helpers.py`
- `assets.pyxres`


---


## [1] Explore the Maze

👾✏️ **Explore the maze, and follow along with the worksheet!** You can use the arrow keys to move around the level.


```shell
python game.py 
```
{{< figure src="images/courses/cs9/unit02/pyxel0.png" width="50%" >}}



---


## [2] Deliverables


{{< deliverables  >}}

{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your changes here"
  > be sure to customize this message, do not copy and paste this line
- git push


{{< /deliverables >}}