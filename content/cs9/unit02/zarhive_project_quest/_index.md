---
Title: Project
draft: true
---

# Unit 02 Games Project

In this project you will make a game using the Quest library. It's up to you to make a game with your group.

{{< figure src="images/courses/cs9/unit02/project0.png" width="70%" >}}

---

## [0] Planning Document

This is a big project with a lot of room for customization. It is important for each group to plan out their game prior to coding.

{{< write-action "Plan your game with your group." >}} Once you have completed your planning document, meet with a teacher to talk through your project.

---

## [1] Deliverables

- A `Unit 02 Games Project: Planning Document` 
- A `project-games` repository will include some if not all the following files:
    - `game.py` when this program runs, it should launch your game
    - map assets
    - sprite assets
    - `.ink` story file
    - `README.md`

### [Timeline]

Click below to see a detailed timeline for your class section.

🕹️ **Our final class of the year will be a party where each group shares their games!**

#### cs9.1
{{< expand "cs9.1 Timeline" >}}

| Date        | Agenda                  |
|-------------|-------------------------|
| 30 May 2022  | Introduction to Project/Planning Doc |
| 02 June 2022 | Work Day        |
| 07 June 2022 | Work Day                |
| 09 June 2022 | Work Day                |
| 13 June 2022 | Due: Final Edits to Game  |
| 16 June 2022 | 🕹️ Final Day of Class - Party 🕹️           |

{{< /expand >}}

#### cs9.2

{{< expand "cs9.2 Timeline" >}}

| Date        | Agenda                  |
|-------------|-------------------------|
| 31 May 2022  | Introduction to Project/Planning Doc |
| 01 June 2022 | Work Day        |
| 02 June 2022 | Work Day                |
| 07 June 2022 | Work Day                |
| 10 June 2022 | Work Day                |
| 14 June 2022 | Work Day                |
| 15 June 2022 | Due: Final Edits to Game                |
| 16 June 2022 | 🕹️ Final Day of Class - Party 🕹️  |

{{< /expand >}}



##  [2] Set Up

For this project, each group will share one git repository. It is your responsibility to regularly commit to your repository.

{{< code-action "Download your repository with starter code for your project." >}}

```shell
cd Desktop
cd cs9/unit_02
git clone https://github.com/the-isf-academy/project-game-group#.git
```
> replace `#` with your group number 

{{< expand "cs9.1 Groups" >}}

| Group #        | Members                  |
|-------------|-------------------------|
| 0  | Chris, Isaac, Edwin |
| 1 | Mina & Charlotte        |
| 2 | Ocean & Dubai                |
| 3 | Nathan  & Alex            |
| 4 | Marcus & Shangyi            |
{{< /expand >}}

{{< expand "cs9.2 Groups" >}}

| Group #        | Members                  |
|-------------|-------------------------|
| 5  | Jonathan, Christopher,  Angus |
| 6 | Shogo & Gabriel        |
| 7 | Lok & Skylar                |
| 8 | Julian & Evan           |
{{< /expand >}}

---

### [Advanced Git]

When using Git as an individual, the primary action is to `push` your work to the server. However, **when multiple people are working on a single project you must remember to `pull` before beginning to code**. 

Communication is key when collaborating on a repository. **We highly recommend communicating with your teammates about who is going to work on which file.** If multiple people edit the same lines of code in the same file, you will have to work together to resolve the merge conflicts. 


Let's practice pushing and pulling by updating the `README.md` file. 

{{< code-action >}} **Choose one person to open the `README.md` file.** 

{{< write-action >}} **Add their name to the file.**

{{< code-action "Save and close the file. Then push the updates to Github" >}}

{{< code-action >}} **Once the changes have been made, the teammate should `git pull` the changes.**

> ```shell
> git pull 
> ```

{{< code-action >}} **The teammate should now open the `README.md` file.** They should see the changes to the file. 

{{< write-action >}} **Add their name to the file.**

---


## [3] General Tips and Tricks

### [Making a Map]

Make sure all of the assets for the map are in the folder of the repository. This includes:

- `.png` tilesets you download from the internet 
- `.tsx` files you create from tilesets in Tiled
- `.tmx` map files you create 

{{< figure src="images/courses/cs9/unit02/project1.png" width="70%" >}}

{{< code-action >}} **Download the map editor, [Tiled](https://thorbjorn.itch.io/tiled)**
> Be sure to select 'No thanks, just take me to the downloads' 

You can find assets to make your map here:
- [https://itch.io/game-assets/free/tag-tilemap](https://itch.io/game-assets/free/tag-tilemap)


---

### [Making Sprites]

You may make your own sprites or find sprites online. Feel free to explore the following resources:
- Make Your Own
    - [https://www.pixilart.com/draw](https://www.pixilart.com/draw)
    - [https://www.piskelapp.com/p/create/sprite](https://www.piskelapp.com/p/create/sprite)
- Pre-made Sprites
    - [https://www.gameart2d.com/freebies.html](https://www.gameart2d.com/freebies.html)
    - [https://craftpix.net/freebies/](https://craftpix.net/freebies/)
    - [https://itch.io/game-assets/free](https://itch.io/game-assets/free)


---
### [TLDR Advanced Github ]

0. `git pull`
0. if you have merge conflicts, resolve them in the files
0. `git status`
0. `git add`
0. `git commit`
0. `git push`

{{< youtube id="__cR7uPBOIk" >}}


---

### [Previous Student Work]

Interested in seeing previous student games? 

Clone the repositories below into your `cs9/unit02` folder:

```shell
git clone https://github.com/the-isf-academy/project-game-sonic.git
```

```shell
git clone https://github.com/the-isf-academy/project-game-ham.git
```

```shell
git clone https://github.com/the-isf-academy/project-game-qwerty.git
```
