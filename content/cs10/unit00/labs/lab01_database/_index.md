---
title: "1. Database"
type: lab
init_action: clone
# draft: true
---

# Lab: Database

In this lab we will learn how to create an SQL (Structured Query Language) database.

{{< figure src="https://img.magnific.com/free-vector/databases-set-three_78370-6669.jpg?semt=ais_hybrid&w=740&q=80" width="25%"  >}}


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

**Our Riddle database is based of this SQL definition.**

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

Now that you understand how the `riddles` are structured as `SQL`, it's up to you use it and re-create the guessing game with a database. First, we will need to write a helper functions to execute SQL.


{{< checkpoint >}}

✏️ **As a class, brainstorm how we will need to access and modify the database for our game.**

{{< /checkpoint >}}


{{< code-action >}} **Open `helpers.py`. Here is where you will write the SQL commands in helper functions.**  There is already one helper function written for you. 


{{< code-action >}} **Write the helper functions we discussed as a class.** Reference the code block below as you're working through each function.

### **[SQL in Python Tips]**

```python
# create connection to the database
db_connection = sqlite3.connect("database.db")

# create cursor to database to access and modify data
db_cursor = db_connection.cursor()

# query for multiple rows of data
all_riddles = db_cursor.execute("SELECT * FROM riddles").fetchall()

# query for one row of data with where
one_riddle = db_cursor.execute("SELECT * FROM riddles WHERE id=1").fetchone()

# query for one row of data with variable
riddle_id = 1
one_riddle = db_cursor.execute("SELECT * FROM riddles WHERE id = ?", (riddle_id,)).fetchone()

# update data for one row of data
db_cursor.execute(f"UPDATE riddles SET answer = 'egg'  WHERE id = 1")

# commit the changes if the data were modified
db_connection.commit()

# Close the connection - you must always do this
db_connection.close()

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


## [4] Extensions 

Choose from these options or think of your own! 

- update riddle difficulty as the stats are updated
- allow users to add new Riddles to the database
    - write a helper function to add a new Riddle by using [insert into](https://www.w3schools.com/sql/sql_insert.asp) 
- Create a `score` table in the existing database 
    - allow uses to add their high score of correct guesses


