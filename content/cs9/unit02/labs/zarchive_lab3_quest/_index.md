---
title: 5. Quest Lab
resources:
- name: Quest
  src: images/courses/cs9/unit02/02_02_quest_island.png
draft: True
---

# Quest Lab

In this lab you explore the Quest framework through a series of mini games. 

Quest helps you build top-down adventure games. You control a player, who walks
around and interacts with the environment, items, and other characters.

## [0] Setup

### [Computer Settings]
Today you will be running a game from your terminal, so your terminal will need permission to monitor your input.
<br>

{{< code-action >}} **Go to Settings > Security &  Privacy > Privacy. Scroll to Input Monitoring and add Terminal.** Terminal to need to restart in order to save this preference.

{{< figure src="images/courses/cs9/unit02/02_02_input_monitoring_permission.png" width="400px" >}}

### [Preparing your Quest]
{{< code-action "Clone the Quest framework and install its requirements." >}}

```shell
cd ~/Desktop/cs9/unit_02
git clone https://github.com/the-isf-academy/quest.git quest_lab
pip3 install --editable quest_lab
cd quest_lab
```



{{< aside "Quest Documentation" >}}

This lab requires you to explore the games, code, and documentation to complete the worksheet.


{{< look-action >}} **Before you to delve into your quest, open up the [Quest documentation](http://cs.fablearn.org/docs/quest).** 


**We recommend one member of your group having the documetnation open and one person having the code/game open.**

Be sure to fill in the checkpoint questions on your worksheet with your group.


{{< /aside >}}

---

## [1] Island Adventure
{{< code-action >}} **Run the first game** You can use the arrow keys or `wasd` to move around the island.

```shell
python3 -m quest.examples.island
```

(Note: We are using the `-m` flag here to tell Python to run the `quest.examples.island` module.)

{{< figure src="images/courses/cs9/unit02/02_02_quest_island.png" width="400px" >}}

---


{{< checkpoint >}}

#### [Exploring features]


{{< write-action >}} This game is made up of a bunch of little images called sprites. The player is a sprite, and each patch of background is a sprite. **How could the game keep track of which background sprites belong where?**

{{< write-action >}} The player is not allowed to walk into the ocean. **How do you think the game enforces this rule?**

{{< write-action >}} **As the player moves around, how does the view adjust to the player’s position? What rule would be applied to get this behavior?**

---

#### [IslandAdventure Properties]

{{< code-action >}} **Open the island.py file**

```shell
atom quest/examples/island.py
```
Note: you can read more about this [on the documentation
  website](http://cs.fablearn.org/docs/quest/_modules/quest/examples/island.html#IslandAdventure)



{{< write-action >}} **What line creates an instance of the IslandAdventure?**

{{< write-action >}} **What line runs the game?**

{{< write-action >}} **What is the parent class of IslandAdventure?**

{{< write-action >}} **What methods does IslandAdventure override?**

{{< write-action >}} The run() method is not in IslandAdventure. **How does IslandAdventure have this method?**



{{< code-action >}} **Play around with the following properties of IslandAdventure, then run the game to see how it is changed.**

```shell
atom quest/examples/island.py
```

{{< write-action >}} **After changing each one, describe how it affects the game.**

- screen_width
- top_viewport_margin
- player_initial_x
- player_speed


---

#### [IslandAdventure vs DiscreteIslandAdventure]
<!-- `QuestGame` has a bunch of methods like `setup_maps()`, `setup_walls()`,
`setup_player()`, `setup_npcs()`, and so on. Most of these do almost nothing.
The idea is that subclasses like `IslandAdventure` can override these methods
when they need to. `IslandAdventure` overrides two methods. -->

{{< code-action >}} **Play the island_discrete.py version of the same game**

```shell
python3 -m quest.examples.island_discrete
```

{{< write-action >}} **What is the definition of discrete? What is the definition of continuous?**

{{< write-action >}} **Compare the movement of the player between IslandAdventure and DiscreteIslandAdventure. What differences do you notice?** *Hint: try walking into a wall.*


{{< code-action >}} **Open the island_discrete.py file:**

```shell
atom quest/examples/island_discrete.py
```


{{< write-action >}} **What method does DiscreteIslandAdventure override to create the difference in movement?**

{{< write-action >}} **Why might a game use discrete movement?**


---

#### [Player Movement]

{{< code-action >}} **Open the game.py file:**

```shell
atom quest/game.py
```


{{< write-action >}} **What are the two methods that handle user input?**

{{< write-action >}} **How does each method affect player movement?**


{{< /checkpoint >}}




---

## [2] Grandma's Soup

{{< code-action >}} **Play grandmas_soup.py**

```shell
python3 -m quest.examples.grandmas_soup
```

{{< figure src="images/courses/cs9/unit02/02_03_quest_island.png" width="400px" >}}


{{< checkpoint >}}
#### [Dialogue]

{{< look-action >}} **Open the** [documentation](http://cs.fablearn.org/docs/quest/examples/grandmas_soup.html) **for Grandma's Soup**

{{< write-action >}} **What is the the Modal class responsible for?**

{{< write-action >}} **What is the the Dialogue class responsible for?**


---

#### [Interactions]

Interactions in the game happen when the main `Player` collides with an `NPC`. `GrandmasSoupGame` extends the `NPC` class into two new classes: `Grandma NPC` and `Vegetable NPC`.

{{< code-action >}} **Open  grandmas_soup.py:**

```shell
atom quest/examples/grandmas_soup.py
```


{{< write-action >}} **What happens when the player collides with Grandma and why?**

{{< write-action >}} **What happens when the player collides with a Vegetable and why?**

{{< write-action >}} **How does the game know when to advance the dialogue? What property does the game use to keep track of the vegetables?**

{{< write-action >}} **Change the messaging of when the game begins and when you collect all the vegetables. How did you make these changes?**

{{< /checkpoint >}}

---

## [3] Extensions

### [Mazes]

{{< look-action >}} **Open the** [documentation](http://cs.fablearn.org/docs/quest/api/maze.html) **for Mazes**

{{< code-action >}} **Play the maze example game:**

```shell
python3 -m quest.examples.maze
```

{{< figure src="images/courses/cs9/unit02/02_04_quest_maze.png" width="400px" >}}


{{< code-action >}} **Enter the python shell**
```shell
python3
```

{{< code-action >}} **Make some sample mazes in a terminal window by running the following code in the python shell:**

*Note: Do not copy the >\>>*

```python
    >>> from quest.maze import Maze
    >>> m = Maze(55, 15)
    >>> m.generate()
    >>> print(m)
```
{{< checkpoint >}}

{{< write-action >}} **What makes a maze a maze? What are its properties?**

{{< write-action >}} **What do the two parameters we pass into the Maze constructor mean?**

{{< write-action >}} **How does the MazeMap class work with the Maze class?**

{{< /checkpoint >}}

---

### [Customizing Games]

Now it’s your turn customize a game! To start, pick something small, just a minor change, so you can get a feel for the framework.

Here are some example features:

* Create a confusing game where the left and right controls are flipped.
* Alter the Maze game so there is more or less treasure.
* Change the treasure sprite in the Maze game.
* Add more items to the GrandmasSoup game.

{{< code-action >}} **Implement your game by creating a new module in the examples directory and extending one of the existing games to add a new feature.**
