---
title: "1. Database"
type: lab
init_action: clone
#draft: true
---

# Lab: Database

In this lab we will learn how to create an SQL (Structured Query Language) database.

{{< figure src="https://www.netgen.co.za/wp-content/uploads/2023/05/SQL-Database.png" width="10%"  >}}


## [0] Setup

{{< code-action "Download DB Browser for SQLite onto your computer:" >}} [sqlitebrowser.org/dl/](https://sqlitebrowser.org/dl/)


{{< code-action  >}} **In the Terminal, go into your `making_with_code` folder and create a `unit03_networking` folder.** 

```shell
cd ~/desktop/making_with_code
mkdir unit03_networking
cd unit03_networking
```


{{< code-action "Then clone your repository" >}} in your `unit03_networking` folder.  Be sure to change `yourgithubusername` to your actual Github username.

```shell
git clone https://github.com/the-isf-academy/lab_database_yourgithubusername
cd lab_database_yourgithubusername
```

{{< code-action "Get the necessary packages:" >}}
```shell
poetry install
```

{{< code-action "Enter the Poetry shell" >}} 
```shell
poetry shell
```
{{< aside "Exiting the poetry shell" >}}
When you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}

📄 **This repository has the following files:**
- `helpers.py`: This file has helper functions that execute SQL
- `game.py`: When run, this file should play the riddle guessing game
- `riddles.sql`: This file stores the structure of the riddles table
- `init_db.py`: This file creates the database and the riddles table
- `database.db`: This is the database file with the riddles table
- `riddles.json`: This is the riddle data that populates the database

{{< code-action "Open the folder in Visual Studio Code" >}} 
```shell
code .
```

---

## [1] Riddles 

**Let's start by exploring the `riddles.sql` file.** This sets up the table for `riddles` and defines each row and its data type. 

```sql
CREATE TABLE IF NOT EXISTS riddles (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    question TEXT NOT NULL,
    answer TEXT NOT NULL,
    total_guesses INTEGER DEFAULT 0,
    correct_guesses INTEGER DEFAULT 0,
    difficulty TEXT DEFAULT 'easy'
);
```


👀 **Take a look at `init_db.py`.** This is where the `database.sql` is created and new rows are added to the riddles table. The riddles are populated from the `riddles.json` file which are cited from [this repo](https://github.com/Code-Institute-Submissions/riddle-1/blob/master/riddles.json).

💻 **Run `init_db.py` to initialize your database.**

💻 **View the database by running `open database.db` in your Terminal** This should open DB Browser for SQLite.
- click `Browse Data`
- make sure `riddles` is selected as the Table

{{< checkpoint >}}

💻 **In DB Browser, select `Execute SQL`**

✏️ **Follow along with the worksheet to explore the database with SQL commands.**

📖 **Here is a helpful [reference of SQL commands](https://www.geeksforgeeks.org/sql-cheat-sheet/).**

{{< /checkpoint >}}

---


## [2] SQL functions

Now that you understand how the `riddles` are structured as `SQL`, it's up to you use it and re-create the guessing game with a database. First, we will need to write a helper funcion to execute SQL.

{{< code-action >}} **Open `helpers.py`. Here is where you will write the SQL queries in helper functions** Two functions are already written for you. 
- `get_all_riddles()`
- `increment_riddle_column(column, id)` 

{{< code-action >}} **Run `helpers.py` to test the helper functions.** Be sure to refresh the database in the `DB Browser` to see Riddle #3 `total_guesses` increase by 1. 
```python
if __name__=="__main__":
    # -- run python helpers.py to test your helper functions
    # use comments to test section by section 

    # gets all Riddles from db and prints each ID and question
    all_riddles = get_all_riddles()
    for riddle in all_riddles:
        print(riddle['id'], riddle['question'])

    # # increments the total_guesses for Riddle #3
    increment_row_value('total_guesses', 3)
```

{{< code-action >}} **You will need to write `get_random_riddles(num)`**

- input: an Integer representing the number of riddles to request 
- output: return a list of random Riddles with the correct number of Riddles

{{< expand "👾 A few helpful SQL commands"  >}}

#### Order by random
```python
conn.execute(
            f"""
            SELECT *
            from riddles
            ORDER BY random()"""
        ).fetchall() 
```

#### Limit number
```sql
conn.execute(
            f"""
            SELECT *
            from riddles
            limit 1"""
        ).fetchall() 
```
{{< /expand >}}

{{< code-action >}} **Test `get_random_riddles(num)` at the bottom of the file.** Be sure to use comments (`#`) to focus on testing specific functions. 


---

## [3] Game

Now that you can access and update the database, you can write re-create the game.

💻 **In `game.py`, re-create the riddle guessing game by using the helper functions that execute SQL.** Be sure to follow this flow chart:



🕹️ **Once you've completed your game logic, play test your game!** `python game.py`

```shell
-----------------------------------
---- Welcome to the Riddler ----
-----------------------------------

Riddle 1: What is black and white and read all over?
Guess: newspaper
Correct :)

Riddle 2: What has to be broken before you can use it?
Guess: A chicken
Incorrect :(

```
---

## [3] Deliverables


{{< deliverables "Congrats on completing the lab!" >}}  

Once you've successfully completed the lab, fill out [this Google form](https://forms.gle/7hpvnzyK5afAiEAp8).


{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push
{{< /deliverables >}}

---

## [4] Extension: Difficulty

Now that we've got a basic riddle guessing game, let's improve it!

It would be great if we could update the `difficulty` based on the `total_guesses` and `correct_guesses` in the database. 

💻 **Incorporate the helper function `updated_difficulty()` into your game.** Based on the ratio of `correct_guesses` to `total_guesses`, it should assign `'easy'`, `'medium'`, or `'hard'` to the `difficulty` row value.

Now, wouldn't it be great if users could customize their game by difficultly.

💻 **Create a helper function `get_riddles_difficulty(difficulty, num_riddles)` into your game.** It should return `num_riddles` riddles of the specific `difficulty`.

💻 **Update your game to include a difficulty selection.**


---

## [5] More Extensions 

Choose from these options or think of your own! 

- Allow users to add new Riddles to the database
    - write a helper function to add a new Riddle by using [insert into](https://www.w3schools.com/sql/sql_insert.asp) 
- Add a category column to the Riddle SQL database 
    - edit the `.sql` file and `init_db.py`
    - incorporate the category into the game 
- Create a `score` table in the database 
    - allow uses to add their high score of correct guesses


