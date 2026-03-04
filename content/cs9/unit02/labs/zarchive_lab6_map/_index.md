---
title: 6. Map Making
draft: True
---

# Map Making

In this lab you explore the map making with [Tiled](https://doc.mapeditor.org/en/stable/). 

{{< figure src="https://www.mapeditor.org/img/screenshot-front.png" width="100%" >}}


--- 

## [0] Setup

{{< code-action >}} **First, download Tiled: [Mac](https://drive.google.com/file/d/1UbyM-hp0IEe4ryz03N5qSaWJkhXb7rJs/view?usp=sharing) or [Windows - requires vpn](https://thorbjorn.itch.io/tiled/download/eyJleHBpcmVzIjoxNjg0MTM1MTMyLCJpZCI6Mjg3Njh9.Q%2bpKwG4sifdwcTmqeuAbCdodS%2b0%3d)**

> For Mac
>   - Download the `.zip` file 
>   - Double click the file
>   - Drag the `Tiled` app into your `Applications` folder

{{< code-action "Then go into your" >}} `unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/unit02_games
```

{{< code-action "Clone your starter code." >}} Be sure to change `yourgithubusername` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab_map_example_yourgithubusername
```

{{< code-action "cd into the lab" >}} 
```shell
cd lab_map_example_yourgithubusername
```

{{< code-action "Enter the Poetry shell and install the requirements:" >}}
```shell
poetry shell
poetry install
```

This repo includes the following files:
- `game_platformer.py`
- `/assets`
    - `/map`
        - `forest_assets.png` - original asset png 
        - `forest_tileset.tsx` - assets in tileset format
        - `forest_map.tmx` - Tiled file
        - `forest_map.tmj` - exported Tiled file for Python file
    - `/sprites`
        - `slime.png` - player image

---

### Finding the Files

First you need to help you computer locate the tileset so that it can load the map in your game. 

{{< code-action >}} **Open this repo in Finder:** 
```shell
open .
```

{{< code-action >}} **Open the `assets/map` folder.** It has the following files:

- `forest_assets.png` - original asset png 
- `forest_tileset.tsx` - assets in tileset format
- `forest_map.tmx` - Tiled file
- `forest_map.tmj` - exported Tiled file for Python file

{{< code-action >}} **Double click the `forest_map.tmx` file to open the map in `Tiled`.**
**There will be an error at the top asking you to find the `forest_tileset.tsx`**

{{< figure src="images/courses/cs9/unit02/arcade09.jpg" width="75%" >}}

{{< code-action >}} **Click `Locate File...` and find `forest_tileset.tsx` in your repository.**    

{{< figure src="images/courses/cs9/unit02/arcade10.jpg" width="75%" >}}

{{< code-action >}} **Click `Open`.** 

{{< code-action >}} **Now save these changes by following these steps:**

1️⃣ `command + s` to save   
2️⃣ `command + shift + e` or `File > Export As` to export   
3️⃣ select `JSON map files (*.tmj *.json)`   
4️⃣ `save`

**Now you are all set to play the game!**

---


## [1] Play the Game
👾 **Play the simple platformer game!** You can use the `W`, `A`, `D` to move around the level. Pressing `esc` will end the game. 

```shell
python game_platformer.py 
```

{{< figure src="images/courses/cs9/unit02/arcade03.png" width="75%" >}}


---


## [2] Exploring Tiled

**Now, return to Tiled to expand and build out the level.**

{{< figure src="images/courses/cs9/unit02/arcade04.png" width="75%" >}}


{{< look-action >}} **Look at each layer on the right hand side.** Use the `eye` tool to hide and show layers.
- Coins
- Walls
- End
- Background

{{< figure src="images/courses/cs9/unit02/arcade05.png" width="50%" >}}

{{< look-action >}} **This map is made up of tiles in the bottom right area of the screen.**

{{< figure src="images/courses/cs9/unit02/arcade06.png" width="50%" >}}

---

### Adding to the map

🎨 **Start by adding more coins to the map!** Double check you editing the the `Coins` layer. 

{{< figure src="images/courses/cs9/unit02/arcade_coin_example.gif" width="75%" >}}

{{< code-action >}} **Save & Export your changes.**
> If you do not *Export As*, you will not see your map changes when you play the game.
0. Save: `command + s`
0. Export As: `command + shift + e` or `File > Export As`
    - Select `JSON map files (*.tmj *.json)`

👾 **Play the game and test your changes:** `python game_platformer.py`. You should see the coins you added! If they do not disapear when your player collides with them, you most likely edited the incorrect map layer. 

---

🎨 **Now, go off and create your own level!** You can change any of the layers
- `Coins` - are tiles the player can collect
- `Walls` - are tiles the player can stand on
- `End` - are the tiles that end the game when the player collides them
- `Background` - are tiles thare are decorative and have no player effects


{{< aside "Export As!" >}}
Don't forget to `Export As` every time you make edits to the map. 

1️⃣ `command + s` to save   
2️⃣ `command + shift + e` or `File > Export As` to export   
3️⃣ select `JSON map files (*.tmj *.json)`   

{{< /aside >}}

👾 **We will play test each other's levels at the end of class!**
> Feel free to edit `game_platformer.py` to experiment with map or game features. A few feature ideas: 
> - A new map layer of spikes that end the game
> - A new map layer that transports the player to another area of the map 
> - A new map layer with an item that boots your movement speed
>
> *These will all require editing the code and the map*  

---

## [3] Deliverables


{{< deliverables  >}}



{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your work here"
  > be sure to customize this message, do not copy and paste this line
- git push



{{< /deliverables >}}


