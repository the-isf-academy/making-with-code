---
title: "2. Database"
type: lab
init_action: clone
# draft: true
---

# Lab: Database

In this lab we will learn how to create an SQL (Structured Query Language) database.

{{< figure src="https://www.netgen.co.za/wp-content/uploads/2023/05/SQL-Database.png" width="10%"  >}}


## [0] Setup

{{< code-action "Download dbsqlite onto your computer:" >}} [sqlitebrowser.org/dl/](https://sqlitebrowser.org/dl/)


{{< code-action "Let's start by cloning the repository" >}} in your `unit03_networking` folder.  Be sure to change `yourgithubusername` to your actual Github username.

```shell
cd ~/desktop/making_with_code/unit03_networking
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

👀 **Take a look at `init_db.py`.** This is where the `database.sql` is created and new rows are added to the riddles table. The riddles are populated from [this repo](https://github.com/Code-Institute-Submissions/riddle-1/blob/master/riddles.json).

💻 **Run `init_db.py` to create your database.**

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

Now that you understand how the `riddles` are structured as `SQL`, it's up to you use it and re-create the guessing game with a database. First, we will need to write helper functions to execute SQL.

{{< code-action >}} **Open `helpers.py`. Here is where you will write the SQL queries in helper functions** Two functions are already written for you. 
- `get_all_riddles()`
- `increment_row_value(column, id)` 

{{< code-action >}} **You will need to write:**
- `get_random_riddles(num_riddles)` - should return `num_riddles` of random riddles 
- `increment_row_value(row, id)` 

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


💻 **Be sure to test your helpers functions at the bottom of the file.** You can execute it by running `python helpers.py`
```python
if __name__=="__main__":
    # -- testing helper SQL functions

    all_riddles = get_all_riddles()
    for riddle in all_riddles:
        print(riddle['id'], riddle['question'])
```

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

Once you've successfully completed the lab, fill out [this Google form](https://forms.gle/HP5Cpp9j4ecrpWVm7).


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

