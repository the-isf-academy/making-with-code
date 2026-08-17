---
title: "1. Terminal"
weight: 20
draft: true
---


# The Terminal: Reloaded
This lab will re-explore one of our most important and most used tools: the Terminal.
The Terminal is what we use to navigate our filesystem, run code files, install software, and
do all kinds of other tasks.

The last time you ventured into the Terminal, you came away with treasure! It's time to dive back into the sea and see what's hiding.

{{< figure src="https://www.kindpng.com/picc/m/410-4102844_transparent-pirate-ship-silhouette-png-pirate-ship-drawing.png" width="75%"  >}}


---

## [0] Setup

{{< aside "Windows Users" >}}
Windows users should use Powershell wherever it says Terminal.

You may see more information output than your Mac peers, but all commands should work the same.
{{< /aside >}}


{{< code-action "First clone the Terminal Adventure Sequel repository" >}}  in your `cs10\unit03_networking` folder. 

```shell
cd ~/desktop/making_with_code/unit03_networking
git clone https://github.com/the-isf-academy/lab_terminal_adventure_sequel
cd lab_terminal_adventure_sequel
```

{{< code-action "Enter the Poetry Shell." >}} Remember, we run this command at the start of each lab, but only when we are inside a lab folder.
```shell
poetry shell
```
{{< aside "Exiting the poetry shell" >}}
When you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}


## [1] Adventure

{{< code-action "Now take a look at what's in the repository:" >}} `ls`
```shell
kitchen	    captain.py     helpers.py    poetry.lock	pyproject.toml
```

> `captain.py` is a runnable Python file (you can tell by the `.py` at the end). *`helpers.py` provides some useful functions that are utilized in this adventure, and `poetry.lock`	and `pyproject.toml` can be ignored.*

{{< code-action  >}} **Run `captian.py` to see what happens! You will end this lab by successfully making a sandwich!** Explore the corners of the kitchen to find the necessary supplies.

{{< figure src="https://www.justonecookbook.com/wp-content/uploads/2020/07/Wanpaku-Sandwich-4986-I-1.jpg" width="75%"  >}}

### Terminal Commands
Below are some Terminal commands which might come in handy on your adventure.


| &nbsp; &nbsp; Command  &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;          | What it does                                 |
| --------------       | -------------------------------------------- |
| `ls`                 | List what's in the current directory.        |
| `cd ~`               | Go to your home directory                    |
| `cd somewhere`       | Go to `somewhere`                            |
| `cd ..`              | Go to the parent directory                   |
| `open file.txt`      | Opens `file.txt` with its default program    |
| `cat file.txt`       | Prints out the contents of `file.txt`        |
| `python x.py`        | Runs the Python program `x.py`               |
| `mv old.txt new.txt` | Renames a file from `old.txt` to `new.txt`. Also works for directories. |
| `mv file.txt dir`    | Moves a file to directory `dir`.             |
| `mv dir1 dir2`       | Moves `dir1` to `dir2` or renames if `dir2` doesn't exist.          |
| `cp old.txt new.txt` | Copy a file from `old.txt` to `new.txt`.     |
| `mkdir bag`          | Creates a new directory called `bag`     |
| `pwd`                | Prints the path to where you are in the filesystem |
| `rm file.txt`        | removes (deletes) the file `file.txt`        |
| `rm -d dir`          | removes (deletes) the directory `dir`        |
| `rm -r dir`          | recursively removes (deletes) the directory `dir` and all subdirectories and files within that directory. **Be careful, this is a powerful tool!** |


## [1] Deliverables


{{< deliverables "Congrats on completing your adventure!" >}}  

Once you've successfully completed the adventure be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSfrb-hH22nHOZbEcZxsCB1XpFyUmTfIHrh2ppvZ18NcytBzkQ/viewform?usp=sf_link).

{{< /deliverables >}}

---

## [2] Extensions
Pick one of the following extensions to continue practicing!

### Continue the Adventure
Delve into the code and try and learn how the Terminal Adventure works. Can you add your own feature?

Some ideas include but are not limited to:
- generating different sandwiches depending on the ingredients in the `sandwich_maker` directory
- adding a new quest from the captain after eating the sandwich
- writing more rooms into the ship for the user to explore


{{< code-action "Expand the current Terminal Adventure!" >}}

### Expand your Turtle drawing from last class
Change directories so that you are in the review lab from last class
```shell
cd ..
cd lab_turtle_review_yourgithubusername
```
{{< code-action >}} **Return to `turtle_drawing.py` and add features so that it now includes all of  the CS concepts below:**
- Variables
- Loops
- Conditionals
- Lists
- Dictionaries
- Functions with parameters

{{< figure src="https://freshgadgets.nl/wp-content/uploads/2014/12/inspirograph2.jpg" width="75%">}}

### Vimtutor
Want to feel like hacker by coding right in your terminal? Type this command in your terminal to launch a tutorial on how to use vim!
```shell
vimtutor
```