---
title: 3. Pyxel Player
# draft: True
---

# Pyxel Player Lab

In this lab you be introduced the Python Pyxel framework by creating a player.

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
git clone https://github.com/the-isf-academy/lab_pyxel_player_YOUR-GITHUB-USERNAME
```

{{< code-action "cd into the lab" >}} 
```shell
cd lab_pyxel_player_YOUR-GITHUB-USERNAME
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
- `helpers.py`
- `assets.pyxres`


---


## [1] Explore `game.py`

💻 **Play the game!** Press `esc` to exit the game. It's quite simple! Today's lab is just about getting used to the Pyxel framework and manipulating the Player. 

```shell
python game.py 
```

{{< checkpoint >}}

✏️ **Follow along with the part 1 of the worksheet to explore how the game is setup and how the Player moves.**

{{< /checkpoint >}}

---

## [2] Explore the Sprite Editor


💻 **Open the Sprite Editor.**  Pyxel has a built in sprite, map, and music editor!

```shell
pyxel edit assets.pyxres
```


{{< figure src="images/courses/cs9/unit02/pyxel0.png" width="50%" >}}

{{< checkpoint >}}

✏️ **Following along with the part 2 of the worksheet to explore how the game is setup and how the Player moves.**

{{< /checkpoint >}}


---


## [3] Deliverables


{{< deliverables  >}}

{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your changes here"
  > be sure to customize this message, do not copy and paste this line
- git push


{{< /deliverables >}}