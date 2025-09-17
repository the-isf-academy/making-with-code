---
title: "4. Fortune"
type: lab
slug: lab_fortune_server

draft: true
---

# Fortune

In this lab we will create a server for a fortune teller. We will delve deeper into design constraints and functionalities of an API. 

{{< figure src="https://m.media-amazon.com/images/I/71DW-Qp7J6L.jpg" width="25%">}}


---

## [0] Set Up


{{< code-action "First, clone the repository" >}} in your `unit03_networking` folder.  Be sure to change `yourgithubusername` to your actual Github username.

```shell
cd ~/desktop/making_with_code/unit03_networking/
git clone https://github.com/the-isf-academy/lab_fortune_yourgithubusername
cd lab_fortuneyourgithubusername
```

{{< code-action "Get the necessary packages" >}}
```shell
poetry install
```


{{< code-action "Enter the Poetry shell" >}}
```shell
poetry shell
```
---

## [1] Add new fortunes

👀 **Look at the definition of the SQL database table in `fortunes.sql`**
> Notice the data types of each column

```sql
CREATE TABLE IF NOT EXISTS fortunes (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    last_updated DATETIME DEFAULT CURRENT_TIMESTAMP,
    fortune TEXT NOT NULL,
    is_happy BOOLEAN NOT NULL,
    num_updates INTEGER DEFAULT 0
);
```


💻 **Open the database file to add a few fortunes:** `open database.db`.


💻 **Add 3 new fortunes using the DB Browser, then save with `⌘+s`.** It's important to have a variety of testing data to ensure the api works as expected. 
- Notice how `booleans` are represented as a `0` or a `1`
{{< figure src="images/courses/cs10/unit00/fortune0.png" alt-text="databases" width=50% >}}



---


## [2] Running the Fortune Server


{{< code-action "Start your local server." >}}
```shell
python api.py
```


💻 **Test the server using `HTTPie`:**  `127.0.0.1:5000/fortune`

👀 **Look at the JSON response in the `help` key and make requests to all of the endpoints.**

```shell
{
  "help": {
    "GET /all": {
      "description": "returns all fortunes",
      "payload": ""
    },
    "GET /new": {
      "description": "adds new fortune to database",
      "payload": "statement: string, is_happy: boolean"
    }
  },
  "overview": "This is the fortune server."
}
```


---


## [3] API

When building an API, it is important to consider how users will interact with it. It is the responsiblity of the developer to design an API with user interaction in mind. 

We want users to be able to:
- filter by the `is_happy` column 
- add on to each other's fortunes 
- delete fortunes if user has the admin key

{{< code-action >}} **Open the `api.py` file.** This server has 2 endpoints:
- `/new`
- `/all`


For each each feature, you will write a helper function to run the SQL commands and then write the endpoint.*


{{< code-action >}} **It is up to you to write the add the following features:**
- `/all` - optional parameter to filter by `is_happy`
- `/update_statement` - add to the end of an exisitng fortune
- `/delete` - delete a fortune with a specific `id` if the `key` is valid 

--- 


### `/is_happy`


{{< code-action >}} **In `helpers.py` write the `get_all_ishappy()` function.** It should use SQL to fetch all riddles filtered on the `is_happy` parameter.
- **parameter:** `is_happy: boolean`

{{< expand "hints" >}}

You may have to cast your argument to boolean like this:

```python
id_happy = bool(request.args['is_happy'])

```
{{< /expand >}}

{{< checkpoint >}}

💻 **Test the function in bottom of `helpers.py`** 

Be sure to test with `False` and `True`. Look at `database.db` to confirm it is working.

```python
all_fortunes = get_all_ishappy(False) 
for fortune in all_fortunes:
  print(fortune['id'])
```
{{< /checkpoint >}}

---


{{< code-action >}} **In `api.py` write the `/is_happy` endpoint.** You should `get_all_ishappy()` function.
- **HTTP method:**  `GET`
- **Params/Payload:**  `is_happy`


{{< checkpoint >}}

💻 **Test the endpoint in the `HTTPie desktop app`**

```shell
http://127.0.0.1:5000/fortune/is_happy is_happy=True
```


✔️ **It should return `json` like:**

```json
{
  "fortunes": [
    {
      "fortune": "you will win money everyday",
      "id": 1,
      "is_happy": true,
      "last_updated": "2025-09-15 04:06:14",
      "num_updates": 1
    },
```
{{< /checkpoint >}}

---

### `/update`

{{< code-action >}} **In `helpers.py` write the `update_fortune()` function.** 
- **parameter:** `id: int, update_string: string`
- It should 
  - add `update_string` to the end of the existing `staetment`
  - increase `num_updates` by 1
  - updated `last_updated` to the current datetime
  - return the updated fortune 

{{< expand "hints" >}}
Remove extra spaces after string
```python
statement = "hello, it is monday "
statement.strip() # returns -> "hello it is monday"

```

Update more than one column
```SQL 
UPDATE fortunes
SET 
  num_updates = num_updates + 1, 
  statement = "updated statement"
WHERE id = 4
```

Get the current datetime in HKT
```SQL
(STRFTIME('%Y-%m-%d %H:%M:%S', 'now', '+8 hours')). 
);
```
{{< /expand >}}


{{< checkpoint >}}

💻 **Test the function in bottom of `helpers.py`**

Refresh the `database.db` file to confirm the fortune is properly updated. 

```python
updated_fortune = update_fortune(1, 'money')
print(updated_fortune['statement'], updated_fortune['num_updates'], updated_fortune['last_updated'] )
```
{{< /checkpoint >}}

---

{{< code-action >}} **In `api.py` write the `/update` endpoint.** 
- **HTTP method:**  `PUT`
- **Payload/args:**  `id:integer`, `update_text:string`
- if the fortune exists 
    - call the `update_fortune()` function
- else  
    - a helpful error message communicating the fortune does not exist 

{{< checkpoint >}}

💻 **Test the endpoint in the `HTTPie desktop app`**

```shell
http://127.0.0.1:5000/fortune/update id=6 update_text=non-stop
```

✔️ **It should return `json` like:**

```json
{
  "message": "Fortune updated successfully",
  "question": {
    "fortune": "tomorrow will rain non-stop",
    "id": 5,
    "is_happy": false,
    "last_updated": "2025-09-16 14:47:33",
    "num_updates": 2
  }
}
```
{{< /checkpoint >}}


---


### `/search`

{{< code-action >}} **In `helpers.py` write the `serach()` function.** 
- **parameter:** `keyword: string`
- return the fortunes from the database that contains the keyword

{{< expand "hint" >}}

Which SQL function is useful to search for a keyword?

You may want to reference [this guide](https://www.w3schools.com/sql/sql_like.asp).

{{< /expand >}}

{{< checkpoint >}}

💻 **Test the function in bottom of `helpers.py`**

```python
all_fortunes = search("win")
for fortune in all_fortunes:
  print(fortune['statement'])
```
{{< /checkpoint >}}

---

{{< code-action >}} **In `apy.py` write the `/search` endpoint.** 
- **HTTP method:**  `get`
- **Payload/args:**  `keyword`
- It should return all fortunes that contain the keyword. 
- If no fortunes exist, provide a helpful error message

🤔 **Consider:**
- Which existing endpoint is similar? 
- How should you format the json that you return?
- What should you return to the user if no fortunes match their search term?

{{< checkpoint >}}

💻 **Test the endpoint in the `HTTPie desktop app`**

```shell
http://127.0.0.1:5000/fortune/search keyword="surprise"
```

✔️ **It should return `json` like:**

```json
{
  "fortunes": [
    {
      "id": 1,
      "statement": "A surprise pizza is coming",
      "num_updates": 1,
      "is_happy": true,
      "last_updated": "2025-09-15 14:06:14",
    },
    {
      "id": 6,
      "statement": "A surprise typhoon day is in your future",
      "num_updates": 1,
      "is_happy": true, 
      "last_updated": "2025-09-13 15:20:13",
    }
    ]
}
```

{{< /checkpoint >}}

---

### `API documentation`

When designing an API, it is important to write helpful documentation so others can use it properly. 

💻 **Look at the current `help` section by making a `GET` request to `/` endpoint in the `HTTPie desktop app`**

```json
{
  "help": {
    "GET /all": {
      "description": "returns all fortunes",
      "payload": ""
    },
    "GET /new": {
      "description": "adds new fortune to database",
      "payload": "statement: string, is_happy: boolean"
    }
  },
  "overview": "This is the fortune server."
}
```

💻 **Add `/is_happy`, `/update`, and `/search` to the `"help"` section of the JSON.**



{{< checkpoint >}}

💻 **Test the endpoint in the `HTTPie desktop app`**

✔️ **It should return `json` like:**

```json
{
  "help": {
    "GET /all": {
      "description": "returns all fortunes",
      "payload": ""
    },
    "GET /new": {
      "description": "adds new fortune to database",
      "payload": "statement: string, is_happy: boolean"
    },
     "GET /is_happy": {
      "description": "returns all fortunes filtered by is_happy",
      "payload": "is_happy: boolean"
    },
     "PUT /update": {
      "description": "adds on to an existing fortune statement",
      "payload": "id: integer, update_text: string"
    },
     "GET /search": {
      "description": "returns all fortunes filtered by a keyword in the statement",
      "payload": "keyword: string"
    }
  },
  "overview": "This is the fortune server."
}
```

{{< /checkpoint >}}


---

## [4] Deliverables


{{< deliverables >}}  

**Once you've successfully completed the worksheet be sure to fill out [this Google form](https://forms.gle/9pihRs3ddfsrPZtv7).**

{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}

---

## [5] Extensions

<!-- - error handling
- archive v. delete 
- URL parameters -->

### Error Handling 

💻 **Try to break your server.**

💻 **Now, add in proper error handling so the server never crashes, but instead provides helpful error messages.**


---

### Archive 

Currently there is no feature to delete a fortune. It can be risky to permanently delete an item from the database, so instead let's utilize the archive column.

💻 **Write a method `toggle_archive()`** that toggles the `archive` field to `True` or `False`, depending on its current state.

💻 **Write a new route `/change_archive` to change the `archive` field of a fortune with a given `id`.**

💻 **Change your exisitng routes (`/all`, `/search`, and `/all/is_happy`) to only return fortunes with `archive` set to `True`.**





<!-- ---

### Calculate Popularity % 

💻 **Create a new field `popularity_percentage` to store the popularity percentage for each `Fortune`.** It should be a `FloatField`. It is up to you to decide how to calculate this percentage. You may want to:
- add additional fields 
- loop through all of the database
 -->


<!-- ---


### Foreign Key

Banjo has the ability to have relational databases. 

```python
from banjo.models import Model, StringField, IntegerField, ForeignKey, BooleanField, FloatField

class Artist(Model):
    name = StringField()


class Song(Model):
    name = StringField()
    artist = ForeignKey(Artist)
```

As Banjo is a wrapper over Django, it works just as the Django documentation states [HERE](https://docs.djangoproject.com/en/4.2/topics/db/examples/many_to_one/).

In the example code above, a **Artist** can be associated with many **Song** objects, but a **Song** object can only have one **Artist** object. 

💻 **Try to incorporate a many-to-one relationship in `models.py`.** An example:
- each `Person` could have many `Fortune` objects.
 -->

