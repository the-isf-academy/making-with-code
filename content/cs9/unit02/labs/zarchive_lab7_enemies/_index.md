---
title: 7. Enemies
draft: True
---

# Enemies

In this lab you explore adding enemies! You will add an enemy into the previous lab `lab_map_example`. 


{{< figure src="https://hips.hearstapps.com/digitalspyuk.cdnds.net/12/48/gaming-super-mario-bros-3.jpg?crop=0.9699372315824248xw:1xh;center,top&resize=1200:*" width="50%" >}}


--- 

## [0] Setup

{{< code-action "Go into the folder" >}} `lab_map_example_yourgithubusername` **folder.** Be sure to change it to your actual Github username. 
```shell
cd ~/desktop/making_with_code/unit02_games/lab_map_example_yourgithubusername
```

{{< code-action "Enter the Poetry shell" >}}
```shell
poetry shell
```

{{< code-action "Open the folder in Visual Studio Code" >}}
```shell
code .
```

---


## [1] Enemy.py


💻 **Create a new file:** `enemy.py`. **Copy and paste this code into the file:**

```python
import arcade
from math import sqrt 


def scale(vector, magnitude):
    # this is helper function 

    vx, vy = vector
    old_magnitude = sqrt(vx * vx + vy * vy) if vx * vx + vy * vy else 0
    factor = magnitude / old_magnitude
    return vx * factor, vy * factor

class Enemy(arcade.Sprite):
    # customize a Sprite for enemy featues 

    def __init__(self, path, scale, center_x, center_y, change_x=None, boundary_left=None, boundary_right=None):
        super().__init__()

        self.scale = scale
        self.center_x = center_x
        self.center_y = center_y
        self.change_x = change_x
        self.boundary_left = boundary_left
        self.boundary_right = boundary_right

        self.textures = []

        # Load a left facing texture and a right facing texture.
        # flipped_horizontally=True will mirror the image we load.
        texture = arcade.load_texture(path)
        self.textures.append(texture)
        
        flipped_texture = arcade.load_texture(path,
                                      flipped_horizontally=True)     

        self.textures.append(flipped_texture)

        # By default, face right.
        self.texture = self.textures[1]

    def update(self):
        # updates the sprite 

        self.position = [
            self._position[0] + self.change_x,
            self._position[1] + self.change_y,
        ]

        self.angle += self.change_angle

        # flip the sprite image
        if self.change_x == 1:
            self.texture = self.textures[0]
        else:
            self.texture = self.textures[1]

        # move the sprite within the boundries
        if self.boundary_left is not None and self.left < self.boundary_left:
            self.change_x *= -1

        elif self.boundary_right is not None and self.right > self.boundary_right:
            self.change_x *= -1


    def on_collison(self, other_sprite):
        # bumps the other_sprite away from itself 

        away = (self.center_x - other_sprite.center_x, self.center_y - other_sprite.center_y)
        away_x, away_y = scale(away, 10)
        other_sprite.center_x = other_sprite.center_x - away_x
        other_sprite.center_y = other_sprite.center_y - away_y
```

---


💻 **Go to the main game file:** `game_platformer.py`

💻 **Add the code below to the top of the file to import the `Enemy`.** 

```python
from enemy import Enemy
```

💻 **Add the code below in the `__init__()`.** This will create one enemy at the location `center_x` and `center_y`. You will need to customize these for your game! 
> *How would you add multiple enemies?* 

```python
# SETS UP ENEMIES
self.enemy_list = arcade.SpriteList()

# enemy with boundries
enemy1 = Enemy(
    path = "assets/sprites/slime.png", 
    scale = 2,
    center_x = 350,
    center_y = 335, 
    change_x = 1, 
    boundary_right= 600,
    boundary_left= 200
    )    

self.enemy_list.append(enemy1)
```

💻 **Add the code below in the `on_draw()` method.** You may want to put it below `self.player_list.draw()`.


```python
self.enemy_list.draw()
```


💻 **Add the code below in the `on_update()` method.** You may want to put it at the top or bottom of the method. 

```python
 # updates the enemies
self.enemy_list.update()

# if the player collides with an enemy
enemies_hit = arcade.check_for_collision_with_list(self.player_sprite, self.enemy_list)
for enemy in enemies_hit:
    enemy.on_collison(self.player_sprite)
```

## [2] Experiment! 

💻 **Experiment with adding enemies into your map!** Here are a few ideas:
- if the player touches an enemy, they moves to the start of the map
- if the player touches an enemy, the game ends 
- add a player_health feature  
    - if a player touches an enemy, the health decreases
    - if the health hits 0, the game ends 

---

## [3] Deliverables


{{< deliverables  >}}



{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your drawing and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push



{{< /deliverables >}}


