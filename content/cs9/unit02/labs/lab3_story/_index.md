---
title: 3. Story Lab
draft: true
---

# Story Lab

In this lab, you are introduced to the structure for writing a branching story. You will use this in your unit project.

{{< figure src="https://img.atlasobscura.com/qekI2cE_2gpQX77Q_jmEcoroTvzMZsTjW4fE6_jlgGk/rt:fit/w:1280/q:81/sm:1/scp:1/ar:1/aHR0cHM6Ly9hdGxh/cy1kZXYuczMuYW1h/em9uYXdzLmNvbS91/cGxvYWRzL2Fzc2V0/cy9kZTE5MWMzZWY5/ODRmMjZiNzdfZWIz/MWJkNzA1M2VjYTA5/M2JjX1RhdHRvbyBN/YXAtMSBjb3B5Lmpw/Zw.jpg" width="75%" >}}



---



## [0] Setup

{{< code-action "Start by going into your" >}} `unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/unit02_games
```

{{< code-action "Clone your starter code." >}} Be sure to change `YOUR-GITHUB-USERNAME` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab_story_example_YOUR-GITHUB-USERNAME
```

{{< code-action "cd into the lab" >}}
```shell
cd lab_story_example_YOUR-GITHUB-USERNAME
```

{{< code-action "Enter the Poetry shell and install the requirements:" >}}
```shell
poetry shell
poetry install
```

This repo includes the following files:
- `game.py`
- `story_setup.py`
- `view.py`
- `model_node.py`
- `model_story.py`

---

## [1] How do you write a story? 

**Stories are made up of connected connected `Node()` objects.**

---

### Node

{{< look-action >}} Let's start by looking at the `Node` constructor:

```python
class Node():
  def __init__(self, id, option_title, description):
      # initializes a node object with its properties

      self.id = id # a unique id
      self.children = []  # a list of node objects
      self.option_title = option_title  # text for display in the menu          
      self.description = description  # text to show if this option is selected
```

It has the following methods:
- `__str__`: defines how a `Node` is printed
- `add_child(child_node)`: this  adds `child_node` to its `children`
  - this is how the story pieces are connected to each other.
- `find(id)` - searches through the nodes to return the node with the `id`
  

---

### Story

**Now, let's look at the `Story()` constructor.** This is the primary class you will be interacting with when writing your story. 
```python
class Story():
  def __init__(self, title, start_id, start_option_title, start_description):
      # initializes a node object with its properties

      self.title = title # the title of your story
      self.current_node = Node(start_id, start_option_title, start_description) #the current Node of your story
      self.first_node = self.current_node # the first Node of your story

```

**A `Story()` has 4 main methods.** Read the comment at the top of each method to know what it does

```python
  def add_new_child(self, parent_id, child_id, child_option_title, child_description):
      # adds a new child node to a parent node
      parent_node = self.current_node.find(parent_id)

      new_child_node = Node(
          id = child_id,
          option_title = child_option_title,
          description= child_description
      )

      parent_node.add_child(new_child_node)

  def get_current_children(self):
      # returns a list of the children of the current node
      return self.current_node.children

  def set_current_node(self,chosen_node):
      # sets the current node to the chosen node
      self.current_node = chosen_node

  def is_finished(self):
      # returns True or False based on if the current node has children
      if len(self.current_node.children) == 0:
          return True
      else:
          return False 
```
---

## [2] Building your first story

{{< look-action >}} **Let's start taking a look at `story_setup.py`** As you can see, the current story has only has 4 unique `Node()` objects and it calls `.add_new_child()` to build the story.

{{< expand "story_setup.py" >}}
```python
from story import Story

def story_setup():
    main_story = Story(
        title='Lunch.',
        start_id = 'lunch',
        start_option_title = "It's lunch time.",
        start_description= "Where will you go?"
    )

    main_story.add_new_child(
        parent_id = 'lunch', 
        child_id = 'bball_court',
        child_option_title='Head down to the basketball court.',
        child_description="It's a nice day, I'd like to go to the basketball court."
        )

    main_story.add_new_child(
        parent_id = 'bball_court', 
        child_id = 'game',
        child_option_title='Play a basketball game.',
        child_description="You see your friends have started playing a game. You join in."
        )

    main_story.add_new_child(
        parent_id = 'lunch', 
        child_id = 'isf_ablock_cafe',
        child_option_title='Walk down to A Block Cafeteria.',
        child_description="You're hungry, better to grab something to eat downstairs."
        )

    main_story.add_new_child(
        parent_id = 'isf_ablock_cafe', 
        child_id = 'optionA',
        child_option_title='Char Siu Rice',
        child_description="Yum, pork!"
        )
```
{{< /expand>}}

{{< code-action >}} **Try to play through the short story in by running:** `python game.py`

```shell
$ python game.py
==================================================
Title: Lunch.

Its lunch time.
Where will you go?
==================================================

[what will you do?]
❯ Head down to the basketball court.
  Walk down to A Block Cafeteria.
```


🧐 *Hmmmmm.... it works, but the story does not continue with your choice.*

---

### Finish game.py

{{< code-action >}} **Finish `game.py` so it properly plays through the story.** It should:

0. show a menu of all the options, and save the choice in a variable 
0. whatever the user chose, set that to the new current node
0. display the description for the new current node
0. loop until there are no more options left

🧐 *Consider...:*
- *What methods exist in the `View()` and `Story()` that you could use?*
- *how do you loop until a condition is met?*

👾 **Be sure to play test the game to ensure it works as expected:** `python game.py`


{{< expand "Example play through" >}}

```

$ python game.py

==================================================
Title: Lunch.

It's lunch time.
Where will you go?
==================================================

[what will you do?] Walk down to A Block Cafeteria.
You're hungry, better to grab something to eat downstairs.

[what will you do?] Char Siu Rice
Yum, pork!


==================================================
End of Story
==================================================

```

{{< /expand >}}

---

### Continue the Story

Now that you've gotten a working `game.py`, let's build out the story. 

Come up with your own options to continue the story! We'll share out at the end of class. 

{{< code-action >}} **"Continue the story, add at least 3 unique `Node()` objects.** Some ideas...
- add additional lunch options in ISF A Block Cafeteria
- add options at the basketball court 
- add other places to go for recess 

👾 **Be sure to play test the game to ensure your story additions work as expected:** `python game.py`

---

## [3] Deliverables

{{< deliverables  >}}

**Once you've successfully completed the game be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSff206imXwF__4FluHsG7rdOOj-lxsIm_xXaQOM05V8sAVEew/viewform?usp=sf_link)**.


{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your drawing and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}


---


## [4] Extensions

For your project, you will need to build out **one** additional feature to this `Story` framework. Here are a few suggested features:
- looping stories with the ability to set an Node as a existing Node's child 
  - *e.g. player can go back to a previous area*
- a `Player` class with unique properties 
  - *e.g. hunger, money, health*
- variable messaging in the story
  - *e.g. `"you have visited this store 5 times"`*
- a special `Node` child-class that gives items or status effects
  - *e.g. a locked door where you need to first collect the key in a certain room.*


{{< code-action >}} **Use this time to experiment with of these features! If you have your own ideas, feel free to experiment with that!**


<!-- ---

## [0] Choose your own Adventure

👾 **Let's start by playing a couple of example choose your own adventure games.** As you play, consider the different genres and what's possible with this structure. 
- [Harry Potter - Sorting Hat](https://unfold.studio/stories/303/)
- [Oregon Trail 1971](https://unfold.studio/stories/10782/)
- [City Exploration](https://unfold.studio/stories/2649/)
- [Store front Example, variables](https://unfold.studio/stories/1065/)

--- -->