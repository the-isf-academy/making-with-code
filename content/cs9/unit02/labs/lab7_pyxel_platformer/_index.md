---
title: 7. Pyxel Platformer Game
draft: False
---

# Platformer Game Lab

In this lab you explore a platformer game and designing tileset.

**📖 You can find the offical documentation [HERE](https://github.com/kitao/pyxel).**

--- 

## [0] Setup



{{< code-action "Start by going into your" >}} `cs9/unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/unit02_games
```

{{< code-action "Clone the repo." >}}  Be sure to change `YOUR-GITHUB-USERNAME` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab_pyxel_platformer_YOUR-GITHUB-USERNAME
```

{{< code-action "cd into the lab" >}} 
```shell
cd https://github.com/the-isf-academy/lab_pyxel_platformer_YOUR-GITHUB-USERNAME
```



{{< code-action "Enter the Poetry shell and install the requirements:" >}}
```shell
poetry shell
poetry install
```

This repo includes these key files:
- `game.py`
- `sprite.py` 
- `player.py`
- `coin.py`
- `helpers.py`
- `assets.pyxres`



---


## [1] Tilesets

💻 **First, play the game `python game.py`.** Note the gravity and notice the walls. There are multiple different tiles that are registered as walls.


💻 **Open the editor**

```shell
pyxel edit assets.pyxres 
```

👀 **Notice, the purple and blue tiles tiles are for the walls.** You can select the tiles on the bottom right. Then, draw with that selection in the map editor. 

{{< figure src="images/courses/cs9/unit02/pyxel1.png" width="25%" >}}

💻 **Go the map editor and add a few walls.** Then save, and replay the game.
{{< figure src="images/courses/cs9/unit02/pyxel2.png" width="50%" >}}

💻 **Open the editer and draw your own wall asset. Then add it to the map.** Be sure to draw it near the other wall tiles.

{{< figure src="images/courses/cs9/unit02/pyxel3.png" width="50%" >}}

💻 **Becuase I added tiles below the exisitng tiles, I will need to find the new x,y cordinate range and edit `helpers.py`** By hovering over the tile on the bottom left, it displays the x,y cordinate on the top.

{{< figure src="images/courses/cs9/unit02/pyxel4.png" width="50%" >}}

💻 **Now, I change the x,y range accordingly in the `helpers.py` file** Remember, `for loops` are exclusive, so you must go 1 above the number.

```python
WALL_TILE_POSITIONS = []
# SET RANGES BASED ON X,Y IN MAP EDITOR
for x in range(0,5):   
    for y in range(2,6):  
        WALL_TILE_POSITIONS.append((x,y))
```    

💻 **Experiment and customize your own tileset!** Feel free to google `tileset pixel example` to reference 

---

## [2] Camera/Gravity


💻 **Experiment with gravity by customizing the attributes in the `Player` class.** 

💻 **Experiment with the camera by experimenting with the `scroll_border_X` and `scroll_border_Y` in the `Game` class.** 


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