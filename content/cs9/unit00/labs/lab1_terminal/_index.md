---
title: "01. Terminal Adventure"

# numberHeaders: true
draft: true

---
# Terminal Adventure
This lab will explore one of the most important tools we'll use all year: the Terminal. The Terminal is what we'll use to navigate our file system, run code files, install software, and
do all kinds of other tasks.


{{< aside "Windows Users" >}}
Windows users should use Powershell wherever it says Terminal.

You may see more information output than your Mac peers, but all commands should work the same.
{{< /aside >}}

---

## [0] Setup

First, we want to make some folders to store our work. Do this we'll be using these three commands:

| Command              | What it does                                 |
| --------------       | -------------------------------------------- |
| `ls`                 | List what's in the current directory (folder).        |
| `mkdir`              | Make a new directory (folder)                   |
| `cd folder`       | Go to `folder`                            |
| `cd ..`       | Go up one to the previous folder                            |

{{< code-action >}} **Open Terminal and use `ls` to list out all the files at your current location.** 

```shell
ls
```

👀 **You should see something like this.**

```shell
Applications         Downloads            Pictures
Creative Cloud       Library              Public
Desktop              Movies
Documents            Music
```

{{< code-action >}} **Then, use `cd` to change directories to your `Desktop`.** A directory is just a fancy word for a folder.

```shell
cd Desktop
```

---

{{< code-action >}} **Use the `mkdir` command to make a directory called `making_with_code`.**  
> `mkdir` stands for *make directory*.

```shell
mkdir making_with_code
```

{{< code-action >}} **Use `ls` to check the folder was created.** 

```shell
ls
```

{{< code-action  >}} **Use `cd` to enter your new `making_with_code` directory.**

```shell
cd making_with_code
```
<!-- 
---

{{< code-action "Make a CS9 folder" >}}

```shell
mkdir CS9
```
{{< code-action "Go into the CS9 folder" >}}

```shell
cd CS9
``` -->

---


{{< code-action  >}} **Make a `unit00_drawing` directory.** This will store your files for our first unit. 

```shell
mkdir unit00_drawing
```
{{< code-action  >}} **Go into the `unit00_drawing` folder**
```shell
cd unit00_drawing
```

---

{{< code-action "Run the following command in your terminal to clone today's lab." >}} This will make a copy of the code on your own computer. *This uses something called `git` and `Github`, you will learn more about this later this unit.*

```shell
git clone https://github.com/the-isf-academy/lab_terminal_adventure.git
```

{{< code-action "Go into the lab_terminal_adventure folder" >}}
```shell
cd lab_terminal_adventure
```

---

{{< code-action "Next, we enter the Poetry shell." >}} This will ensure all of the correct packages and versions of those packages are being used. 
> You will use `poetry shell`, everytime you want to work on a lab or project. 
```shell
poetry shell
```
> You should see the following output:
> ```shell
> Creating virtualenv lab-00-terminal-adventure-shGU1wL6-py3.10 in /Users/eqbrown/Library/Caches/pypoetry/virtualenvs
> Spawning shell within /Users/eqbrown/Library/Caches/pypoetry/virtualenvs/lab-00-terminal-adventure-shGU1wL6-py3.10
>bash-5.1$ . /Users/eqbrown/Library/Caches/pypoetry/virtualenvs/lab-00-terminal-adventure-shGU1wL6-py3.10/bin/activate
>(lab-00-terminal-adventure-shGU1wL6-py3.10) bash-5.1$

{{< aside "Exiting the poetry shell" >}}
When you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}

📁 **Your folders are now all properly setup for `cs`!**

---

## [1] Starting your Adventure

{{< code-action >}} **If you left the poetry shell, make sure you enter it again.** 
```shell
poetry shell
```

{{< code-action >}} **Let's have a look at what's in the `lab_terminal_adventure` repository with `ls`.** A *repository* is just a fancy word for a folder that is stored in the cloud using a version control software. 
```shell
ls
```
> You should see the following output:
> ```shell
> adventure	    returnToShip.py  poetry.lock	pyproject.toml
> ```
> `returnToShip.py` is a runnable Python file (you can tell by the `.py` at the end).

{{< code-action "Run it to see what happens:" >}}

```shell
python returnToShip.py

```
> You should see the following output:
> ```shell
>Your adventure has only just begun. You are not yet ready to return
>to the ship. More secrets await you in the ocean's depths.
>```

{{< aside "Your challenge is to see if you can get the treasure, using just the Terminal" >}}

Use Terminal to explore the contents of the `adventure` directory.

{{< /aside >}}



{{< code-action "Begin by going into into the" >}}  `adventure` **directory:**

```shell
cd adventure
ls
```
> You should see the following output:
> ```shell
>seafloor	sinking.txt
>```

`sinking.txt` is a text file, so we can read it.

{{< code-action "Try using the " >}} `cat` **command:**

```shell
cat sinking.txt
```


{{< code-action >}} **Continue exploring into the depths of the sea to find the treasure!** Return to the `lab_00_terminal_adventure` directory and run the `returnToShip.py` file to see if you were successful. If you were unable to escape the monster, try again!


{{< figure src="https://sealifeart.co.uk/wp-content/uploads/2019/11/treasure-chest-drawing.jpg" width="25%"  >}}

---


### Terminal Commands
Below are some Terminal commands which might come in handy on your adventure.


| &nbsp; &nbsp; &nbsp; &nbsp; Command &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;| What it does                                 |
| --------------       | -------------------------------------------- |
| `ls`                 | List what's in the current directory.        |
| `cd ~`               | Go to your home directory                    |
| `cd folder`       | Go to `folder`                            |
| `cd ..`              | Go up a level in your directory system.                  |
| `open file.txt`      | Opens `file.txt` with its default program    |
| `cat file.txt`       | Prints out the contents of `file.txt`        |
| `python x.py`        | Runs the Python program `x.py`               |
| `mv old.txt new.txt` | Renames a file from `old.txt` to `new.txt`. Also works for directories. |
| `mv file.txt dir`    | Moves a file to directory `dir`.             |
| `mv dir1 dir2`       | Moves `dir1` to `dir2` or renames if `dir2` doesn't exist.          |
| `mv dir1 ..`       | Moves `dir1` up a level in your directory system.          |
| `cp old.txt new.txt` | Copy a file from `old.txt` to `new.txt`.     |
| `mkdir bag`          | Creates a new directory called `bag`     |
| `pwd`                | Prints the path to where you are in the filesystem |
| `rm file.txt`        | removes (deletes) the file `file.txt`        |
| `rm -d dir`          | removes (deletes) the directory `dir`        |
| `rm -r dir`          | recursively removes (deletes) the directory `dir` and all subdirectories and files within that directory. **Be careful, this is a powerful tool!** |

{{< expand "More Terminal Commands" >}}
These are just for fun. There's lots more--ask your teachers!

| Command              | What it does                                 |
| --------------       | -------------------------------------------- |
| `say hello`          | Makes the computer say hello (Mac only)      |
| `cat sinking.txt \| say` | Makes the computer read the text file aloud |
| `cal`                | Shows you a monthly calendar                 |
| `banner hello`       | Just try it                                  |

{{< /expand >}}


---


## [2] Deliverables


{{< deliverables "You will end this lab by collecting the treasure!" >}}
✔ **Once you've successfully completed the adventure be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSdE8uL3aKClQNZBSrfb2mD5ZkvNXGrq47v3lC2kr8K95LJdOw/viewform?usp=sf_link)**.


{{< /deliverables >}}

{{< aside "Exiting the poetry shell" >}}
Remember, when you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}



---

## [3] Extension

{{< code-action >}} **Once you finish the Terminal Adventure, you may either explore `Vim` OR continue exploring drawing with the Python Turtle library.**


{{< columns >}}
### Vim

Vim is text-editor that you can use to write code directly inside your Terminal. Ms. Brown or Ms. Genzlinger may have used `vim` to activate `Poetry` on your computer. 

**💻 To learn `vim`, in your Terminal type:**
> *You can create a new `tab` in your terminal with `⌘+t`*
```shell
vimtutor
```

Vimtutor is a built in tutorial for learning `vim`.

<--->

### Python Turtle


💻 **Go to [bit.ly/day1_cs9](https://trinket.io/python/196e77f175) and continue experimenting with Python code.** Can you figure out how to: 
- draw a polygon of any number of sides? *(triangle, hexagon, etc.)*
- draw the [olympic rings](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5c/Olympic_rings_without_rims.svg/1200px-Olympic_rings_without_rims.svg.png)
- draw a [bullseye](https://compucademy.net/wp-content/uploads/2021/05/python-turtle-archery.png)

{{< /columns >}}


