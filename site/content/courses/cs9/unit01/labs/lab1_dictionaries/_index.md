---
title: 1. Dictionaries
type: lab
# draft: True

---

# Dictionaries 

In this lab, we will learn about dictionaries, another useful data structure. 

## [0] Setup


{{< code-action >}} Start by cloning your `lab-dictionaries` repository in your `cs9` folder. 
```shell
cd desktop/cs9/unit_01
git clone https://github.com/the-isf-academy/lab-dictionaries-YOUR-GITHUB-USERNAME.git
```

## [1] High π Useful Data Structure

You already know about lists, which are a great way to store things that naturally come one after another, like subway stops on a subway line, or homework assignments in a class. 

The structure of a list works well for things that have a natural order (like zodiac cycles), but what about things that don't have a natural order to them?

A **dictionary is another kind of data structure that is useful for information that does not have a natural order.** 

**Dictionaries connect keys to values**. For each unique key (for example, an animal name like `'pig'`), a dictionary stores a unique value (like a translation `ηͺ`). 


```python
animal_dict = {
"rat": "ιΌ ",
"ox": "η",
"tiger": "θ",
"rabbit": "ε",
"dragon": "ιΎ",
"snake": "θ",
"horse": "ι©¬",
"sheep": "ηΎ",
"monkey": "η΄",
"rooster": "ιΈ‘",
"dog": "η",
}
```

**Values in a dictionary are accessed via the key.** For example:
```python3
animal_dict['dog']
```

> Will return:
> ```python3
> 'η'
> ```

**Keys can easily be added to a dictionary like so:**
```python3
animaion_dict["pig"] = "ηͺ"
```


**You can loop through a `dict` in almost the same way you can loop through a list:**

```python3
for english, chinese in animal_dict.items():
  print("English zodiac: {} - Chinese zodiac: {}.".format(english, chinese))
```

> Will output:
> ```python3
> English zodiac: rat | Chinese zodiac: ιΌ .
> English zodiac: ox | Chinese zodiac: η.
> English zodiac: tiger | Chinese zodiac: θ.
> English zodiac: rabbit | Chinese zodiac: ε.
> English zodiac: dragon | Chinese zodiac: ιΎ.
> English zodiac: snake | Chinese zodiac: θ.
> English zodiac: horse | Chinese zodiac: ι©¬.
> English zodiac: sheep | Chinese zodiac: ηΎ.
> English zodiac: monkey | Chinese zodiac: η΄.
> English zodiac: rooster | Chinese zodiac: ιΈ‘.
> English zodiac: dog | Chinese zodiac: η.
> English zodiac: pig | Chinese zodiac: ηͺ.
>   ```

### [Zodiac Year]


{{< code-action "Let's run the file" >}} `zodiac_year_finder.py`. It's inside the `/introduction` directory. Currently, it only tell you your zodiac in English. 


```shell
> python3 zodiac_year_finder.py
What is your birth year? 2010
I was born in the year of the tiger.
```

{{< code-action "Use the" >}} `animals_dict` **to add the Chinese translation to the English Sentence** *"I was born in the year of the ________".*


> Your `zodiac_year_finder.py`  should now output something like:
> ```shell
> I was born in the year of the tiger.
> ζε±θ
>```


## [2] Game Library

Let's imagine our school had a library of video games. We could use a `dictionary` and `lists` to organize each game by genre.

```python
game_library_dict = {
    "Sports": ["Fifa", "NBA 2K", "Wii Sports"],
    "Puzzle": ["Sodoku", "Tetris", "Bejeweled","Mahjong"],
    "Multiplayer": ["Amoung Us","Fall Guys","Minecraft","Fortnite","Rocket League"],
    "RPG" : ["The Witcher 3","Skyrim", "World of Warcraft", "Persona 5", "The Legends of Zelda"]
}
```
> *Notice:*
> - *each `key` is a `string` type*
> - *each `value` is a `list` of `string` types*

It's up to you, to write functions that will return information about the `game_library dict`.

**You will code the following functions in the `library_functions.py`:**
- `total_num_games()`
- `get_genres()`
- `num_games_per_genre()`
- `get_games_for_genre()`

{{< figure src="images/courses/cs9/unit01/01_dict_function_diagram.png" width="600px">}}




{{< code-action >}} `total_num_games()`
- Paramter: a dictionary 
- Return value: an integer value representing the number of games in the given dictionary 

{{< code-action >}} `get_genres()`
- Paramter: a dictionary 
- Return value: a list of the genres available in a given dictionary 

{{< code-action >}} `num_games_per_genre()`
- Paramters: a genre, a dictionary 
- Return value: an integer value representing the number of games available for the given genre in the given dictionary

{{< code-action >}} `get_games_for_genre()`
- Paramter: a genre, a dictionary 
- Return value: a list of games available for the given genre in the given dictionary

<br>

A helpful function:

| Function  | Explanation  |  Example |
|:-:|:-:|:-:|
| keys() | returns the keys in a dictionary  |  my_dict.keys() |


### [Testing]

{{< code-action "Write tests to ensure each of your functions works as intended." >}} Use `library_test.py` to test your functions sufficiently. 


{{< checkpoint >}}
Answer the following prompts in your notebook before submitting this lab:

0. What is a dictionary and why is it useful? 
0. How would you use a dictionary to organize students by grade level? 
0. Look at the "0. Planet Gravity" Do Now. How could you use a dictionary to better organize the information?


{{< /checkpoint >}}

### [Deliverables]
{{< deliverables >}}
{{< code-action >}} **For this lab, you should `push` updates to the following files to Github.**

- `lab-dictionaries` respository
    - `zodiac_year_finder.py`
    - `library_functions.py`
    - `library_test.py`

Also be sure to hand in your notebook with checkpoint questions.
{{< /deliverables >}}

## [3] Extensions: Interactive Games Library 

Now that you've written the `library_functions`, it's up you to put them to good use. 

{{< code-action "Create a new file called," >}} `interactive_library.py`


{{< code-action "Write an interactive games library that includes, but is not limited to, the following functionalities:" >}} 
- viewing the total number of games
- viewing the genres 
- viewing the games by genre 

{{< code-action "Write a new file called," >}} `interactive_library.py`


*Here is an example:*
```shell
------------------------------------
--Welcome to the CS Game Library--
------------------------------------

We have 17 total games.

We have the following genres:
  - Sports
  - Puzzle
  - Multiplayer
  - RPG

Select a genre to view the games available: Sports

We have 3 Sports games:
  - Fifa
  - NBA 2K
  - Wii Sports

------------------------------------
--------Thanks for visiting!--------
------------------------------------
```

{{< code-action >}} **Be sure to `push` your new file to Github.**


### [Contributing to the library]

How would you adjust your program to allow users to add games to the library? 
> *Consider:*
> - How would you implement a menu system?
> - How do you add things to a dictionary?


{{< code-action "Add a functionality that allows users to add games to the library." >}} 

{{< code-action >}} **Remember to `push` your work to Github.**
