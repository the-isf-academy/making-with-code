---
title: 7. Pyxel Platformer Game
draft: True
---

# Platformer Game Lab

In this lab you explore a Platformer game and designing tileset.

**📖 You can find the official documentation [HERE](https://github.com/kitao/pyxel).**

--- 

## [0] Setup



{{< code-action "Start by going into your" >}} `unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/unit02_games
```

{{< code-action "Clone the repo." >}}  Be sure to change `YOUR-GITHUB-USERNAME` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab_pyxel_platformer_YOUR-GITHUB-USERNAME
```

{{< code-action "cd into the lab" >}} 
```shell
cd lab_pyxel_platformer_YOUR-GITHUB-USERNAME
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
- `camera.py`
- `assets.pyxres`



---


## [1] Tilesets

💻 **First, play the game `python game.py`.** Use the arrows `<` `>` to move sideways and `space` to jump. Note the gravity and note the walls. There are multiple different tiles that are registered as walls.


---
### Edit the Map

💻 **Open the resource editor**

```shell
pyxel edit assets.pyxres 
```

👀 **Go to the map editor. Notice, the purple and blue tiles are all solid walls.** You can select the tiles on the bottom right. Then, draw with that selection in the map editor.

{{< figure src="images/courses/cs9/unit02/pyxel1.png" width="25%" >}}

💻 **Add some new walls to the map.**  Then save, and replay the game.
{{< figure src="images/courses/cs9/unit02/pyxel2.png" width="50%" >}}

---

### Add Your Own Tiles

💻 **Open the editor and draw your own wall asset.**  Be sure to draw it near the other wall tiles.     


{{< figure src="images/courses/cs9/unit02/pyxel3.png" width="50%" >}}

💻 **Then add your new tile into the map.**   

<br>

{{< aside "Setting New Tiles as WALLS" >}}

When new `WALL` tiles are added, you must update the code accordingly. 

👀 ✏️ **Find the new x,y coordinate range of the WALL tiles.** By hovering over the tile on the bottom left, it displays the x,y coordinate on the top.    
<br>
In the screenshot, the new tile is located at `(0,5)`

{{< figure src="images/courses/cs9/unit02/pyxel4.png" width="50%" >}}

💻 **In `helpers.py`, update the x,y range accordingly to your new tile range.** Remember, in `for i in range(start, stop)` the `stop` value is not inclusive. So your `stop` value must be **+1** above your desired number.

```python {linenos=table, hl_lines=["4"],linenostart=33}
WALL_TILE_POSITIONS = []
# SET RANGES BASED ON X,Y IN MAP EDITOR
for x in range(0,5):   
    for y in range(2,6):  
        WALL_TILE_POSITIONS.append((x,y))
```    

{{< /aside  >}}

💻 **Experiment and customize your own tileset!** Feel free to google `tileset pixel example` to reference 

---

## [2] Camera/Gravity


💻 **Experiment with gravity by customizing the attributes in the `Player` class.** 


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
- remote

{{< /deliverables >}}