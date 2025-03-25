---
title: 5. Story Lab [extended]
# draft: true
---

# Story Lab [extended]

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
git clone https://github.com/the-isf-academy/lab_story_extended_YOUR-GITHUB-USERNAME
```

{{< code-action "cd into the lab" >}}
```shell
cd lab_story_extended_YOUR-GITHUB-USERNAME
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

{{< look-action >}} Let's start by looking at the `Node` class:

{{<mermaid align="left">}}
classDiagram
    class Node {
        +id: str 
        +option_title: str
        +description: str
        +children: [] Node
        +Node(id, option_title, description)
        +__ str __(): str
        +__ repr __(): str
        +add_child(Node)
        +find(id): Node
    }
{{< /mermaid >}}

A few things to take note of:
- The `Node()` method is to describe how to create a Node - it requires 3 arguements
- `__str__()`: defines how a `Node` is printed
- `__repr__()`: defines how a `Node` is represented (this will help with debugging)
- `add_child(child_node)`: this  apends `child_node` to its `children`
  - this is how the story pieces are connected to each other.
- `find(id)` - searches through the Nodes to return the Node with the `id`
  

---

### Story

**Now, let's look at the `Story()` class.** This is the primary class you will be interacting with when writing your story. 


{{<mermaid align="left">}}
classDiagram
    class Story {
        +title: str 
        +first_node: Node
        +current_node: Node
        +Story(title, first_id,first_option_title, first_description)
        +get_current_node(): Node
        +get_current_children(self): [] Node
        +chosen_node(current_node)
        +add_new_children(parent_id, child_title, child_option_title, child_description)
        +is_running(): Boolean

    }
{{< /mermaid >}}

A few things to take note of:
- `first_node` - is a Node created from the arguements when a Story is created
- `current_nodde` - when a Story is created, holds `first_note` - this changes as the Story progresses 
- `add_new_children()` is used to to add new paths to your story

---

### Setting up a Story

👀 **Let's start taking a look at `story_setup.py`** As you can see, the current story has only has 4 unique `Node()` objects and it calls `.add_new_child()` to build the story.

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

---

## [3] Implementing the Game Loop

Now that we have a simple story, let's create the game loop so a user can play through it. 

{{< code-action >}} **Implement the game loop flow chart in `game.py` so it properly plays through the story.** 

{{< figure src="images/courses/cs9/unit02/story0.png" width="50%" >}}


🧐 *Consider...:*
- *Try testing the classes before you implement the game*
- *What methods exist in the `View()` and `Story()` that you should use?*
- *How do you loop until a condition is met?*

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

{{< code-action >}} **Continue the story, add at least 3 unique `Node()` objects.** Some ideas...
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