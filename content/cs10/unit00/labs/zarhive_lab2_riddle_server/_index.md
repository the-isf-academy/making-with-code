---
title: "2. Banjo Server"
type: lab
slug: lab_riddle_server

draft: true
---

# Riddle Server

In this lab we are going to learn how the riddle server is made using Banjo.

📖 **Open the Banjo documentation:** [the-isf-academy.github.io/banjo_docs/](https://the-isf-academy.github.io/banjo_docs/)

{{< expand "Debugging" >}}

**If you are getting an "Access Denied" error when visiting the `/api` route:**

0. Go to this url: `chrome://net-internals/#sockets`
0. Select "Flush socket pool"
0. Refresh the page

{{< /expand >}}


---

## [0] Set Up

{{< code-action "Download Mac app of HTTPIE:" >}} [ httpie.io/download](https://httpie.io/download). We need to download the app to make local HTTP requests for testing purposes. In this lab, you will run a locally hosted riddle server on your laptop using Banjo.

{{< figure src="https://httpie.io/Images/download-shape.svg" width="25%">}}



{{< code-action "Start by going into the unit folder and the lab." >}} Remember to replace `yourgithubusername` with your actual GitHub username.
```shell
cd ~/desktop/making_with_code/unit03_networking/
cd lab_banjo_yourgithubusername
```


{{< code-action "Upgrade versions" >}}
```shell
poetry update
```

{{< code-action "Enter the Poetry shell" >}}
```shell
poetry shell
```


---
## [1] Local Riddle Server

You are each able to run a locally hosted riddle server on your laptop using Banjo.

### Starting the Server

{{< code-action "Now, let's start your local server." >}} We use `--debug` to provide more information when in the development stage.
```shell
banjo --debug
```
```shell
No changes detected in apps 'app', 'banjo'
Operations to perform:
  Apply all migrations: admin, app, auth, contenttypes, sessions
Running migrations:
  No migrations to apply.
No changes detected in apps 'banjo', 'app'
Operations to perform:
  Apply all migrations: admin, app, auth, contenttypes, sessions
Running migrations:
  No migrations to apply.
Performing system checks...

System check identified no issues (0 silenced).
September 16, 2022 - 02:40:21
Django version 4.1.1, using settings 'banjo.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

---


### Accessing the Server

💻 **You can now visit this server in your web browser, just as you did with the riddler server hosted on the internet:**  [127.0.0.1:8000/riddle/all](http://127.0.0.1:8000/riddle/all)

💻 **Open the `HTTPie` desktop app to send the same `GET` request to `/all`.**

{{< figure src="images/courses/cs10/unit00/banjo_server_00.png" width=50%" >}}


{{< look-action " Look at the Terminal window running the server. Notice how it recorded your request." >}}
```shell
[16/Sep/2024 02:44:20] "GET /riddle/all HTTP/1.1" 200 1069
```

---

💻 **Send a `POST` request to the `/new` endpoint.** 
> Payload:
> - `question` (str)
> - `answer` (str)

{{< figure src="images/courses/cs10/unit00/banjo_server_01.png" width=50%" >}}

{{< expand "Getting a 400 Error?" >}}

Make sure you did all these steps: 

0. Change `all` to `new` in the url
0. Change `GET` to `POST`
0. Change `Params` to `Body`
0. At the bottom, change `None` to `Form`
0. Add the *payloads:* `question` and `answer`

{{< /expand  >}}

{{< look-action " Look at the Terminal window running the server. Notice how it recorded your request." >}}
```shell
[01/Sep/2024 20:56:22] "POST /riddle/new?id=1 HTTP/1.1" 200 127
```

---

Your version of the riddle server only has the 2 endpoints:
- `/riddle/all`
- `/riddle/new`

{{< checkpoint >}}

{{< code-action "Explore both endpoints via the HTTPie desktop app and be sure to successfully:" >}}
- view all riddles without the answers
- create a new riddle
{{< /checkpoint >}}

---

## [2] What is Banjo?

**This server is written using [Banjo](https://cs.fablearn.org/docs/banjo/index.html)**, a wrapper for [Django](https://www.djangoproject.com/). It allows users to quickly create models with a persistant database and API.

📁 **Banjo apps must have an `app` folder. Within the app folder must be two files: `models.py`, `views.py`.** The `database.sqlite` file is created when the server is first started. It is stored at the same level as `app`. Here is an example file structure:
```shell
lab_banjo
|
└──app
|   ├──models.py
|   └──views.py
└──database.sqlite
```
- `models.py` - This defines what the database will look like. Models are a lot like classes. Just as a class has properties, a model has fields. When defining a model's fields, you must specify the data type.
- `views.py` - The views are where you define the API functionality. Here is where you decide what the `endpoints` are and the type of `HTTP` request it will require.

📄 **In this lab, we are going to be primarily focused on the `views.py` file.**

---

## [3] Writing Routes

In this lab, you will build out the functionality of the Riddle server. Currently, your file only has `riddle/all` and `riddle/new`. 

**It is up to you to add the following endpoints:**
- `riddle/one`
- `riddle/guess`
- `riddle/difficulty`
- `riddle/random`

 <br>

{{< code-action "Start by opening up the primary folder:" >}} `/app`

```shell
code app
```

{{< aside >}}
Open a new terminal tab using `⌘ + T`.   
You can have your server running in one tab, and use the other tab to access your filesystem.
{{< /aside >}}
 <br>

{{< code-action >}} **Open the `views.py` file.** Here is where you will write the additional endpoints. 

📖 **Open the Banjo Views Documentation: [the-isf-academy.github.io/banjo_docs/](https://the-isf-academy.github.io/banjo_docs/)** You will need to reference this and the exisiting routes in `views.py`.

<!-- 🌐 **You may also want to reference the Riddle server that is live on the web:** [sycs.student.isf.edu.hk/riddle](http://sycs.student.isf.edu.hk/riddle). This is a unique route `/api` that provides a basic frontend interaction with the API. -->

---

### riddle/one

{{< code-action >}} **Write the `riddle/one` endpoint.** 
- **HTTP method:** `get`
- **Payload/args:** `id`
- **Return:** a single `Riddle` with the `question`, `guesses`, and `correct` properties


🤔 *Which `method` in the `Riddle` `model` could be useful?*

{{< checkpoint >}}

💻 **Test the `riddle/one` endpoint in the `HTTPie desktop app`**

```shell
http://127.0.0.1:8000/riddle/one
```


✔️ **It should return `json` like:**

```json
{
  "riddle": {
    "id": 1,
    "question": "I’m light as a feather, yet the strongest person can’t hold me for five minutes. What am I?",
    "guesses": 43,
  "correct": 1
  } 
}
```

{{< /checkpoint >}}

---

### riddle/guess

{{< code-action >}} **Write the `riddle/guess` endpoint.** 
- **HTTP method:**  `post`
- **Payload/args:**  `id` and `guess`
- **Return:** 
  - if the guess was correct
    - message telling the user they were correct
    - a single `Riddle` with the `id`, `question`, `guesses`, `correct`, and `answer` properties
  - if the guess was incorrect
    - message telling the user they were incorrect
    - a single `Riddle` with the `id`, `question`, `guesses`, and `correct`, properties

🤔 *Which `method` in the `Riddle` `model` could be useful?*


{{< checkpoint >}}

💻 **Test the `riddle/guess` endpoint in the `HTTPie desktop app`**

```shell
http://127.0.0.1:8000/riddle/guess
```

✔️ **It should return `json` like:**

```json
{
  "riddle": {
    "id": 1,
    "question": "I’m light as a feather, yet the strongest person can’t hold me for five minutes. What am I?",
    "guesses": 44,
    "correct": false
  }
}
{{< /checkpoint >}}

---


### riddle/difficulty

{{< code-action >}} **Write the `riddle/difficulty` endpoint.** 
- **HTTP method:** `get`
- **Payload/args:** `id`
- **Return:** 
    - a single `Riddle` with the `id`, `question`, and `difficulty` properties

🤔 *Which `method` in the `Riddle` `model` could be useful?*


{{< checkpoint >}}

💻 **Test the `riddle/difficulty` endpoint in the `HTTPie desktop app`**

```shell
http://127.0.0.1:8000/riddle/difficulty
```

✔️ **It should return `json` like:**

```json
{
  "riddle": {
    "id": 1,
    "question": "I’m light as a feather, yet the strongest person can’t hold me for five minutes. What am I?",
    "difficulty": 0.9555555555555556
  }
}
```

{{< /checkpoint >}}

---

### riddle/random

{{< code-action >}} **Write the `riddle/random` endpoint.** 
- **HTTP method:**`get`
- **Payload/args:** none
- **Return:**  a single `Riddle` with the `id`, `question`,  `correct`, and `guess` properties 

🤔 *Which query method may be useful? Be sure to reference the [Banjo documentation](https://cs.fablearn.org/docs/banjo/index.html).*


{{< checkpoint >}}

💻 **Test the `riddle/random` endpoint in the `HTTPie desktop app`**

```shell
http://127.0.0.1:8000/riddle/random 
```

✔️ **It should return `json` like:**

```json
{
  "riddle": {
    "id": 6,
    "question": "The more you take, the more you leave behind. What am I?",
    "guesses": 4,
    "correct": 0
  }
}
```
```

{{< /checkpoint >}}

---

## [4] Deliverables


{{< deliverables >}}  

**Once you've successfully completed the worksheet be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSchvEidsL2yaQuPA09E78HCAqlee7X7nhgys72ib9dtCl-Y6A/viewform?usp=sf_link).**

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


### View Solution

Currently, there's no way to see the answer unless you correctly guess the riddle. 

{{< code-action >}} **Write an endpoint that has the ability to view the solution of a given Riddle.** 
- *an existing `Riddle` method may be useful*

It should return `JSON` that looks something like:
```json
{
    "riddle": [
        {
            "correct": 0,
            "guesses": 3,
            "id": 1,
            "question": "It goes up and down the stairs without moving.",
            "answer": "A carpet"
        }
    ]
}
```

---
### Change Question and Answer

{{< code-action >}} **Write an endpoint that has the ability to change the question a riddle.** 
- *It may be helpful to write a new method `change_question()`


| Method | URL                                | Required Payload     | Action                                                                                   |
| ------ | ---------------------------------- | -------------------- | ---------------------------------------------------------------------------------------- |
| `POST`  | `/change/question`   |        new_question             | Returns thee riddle with the new answer    |

{{< code-action >}} **Write an endpoint that has the ability to change the answer of a riddle.** 
- *It may be helpful to write a new method `change_answer()`

| Method | URL                                | Required Payload     | Action                                                                                   |
| ------ | ---------------------------------- | -------------------- | ---------------------------------------------------------------------------------------- |
| `POST`  | `/change/answer`   |        new_answer             | Returns the riddle with the new answer    |

---

### Difficulty Level Endpoint 

Because we track `difficulty`, it would be nice if we could `GET` a list of riddles of `easy`, `medium,` or `hard` difficulty. 

{{< code-action >}} **Write an endpoint returns riddles within a difficulty category** 
- *a Riddle with a difficulty of 1 is impossibly hard, while a Riddle with a difficulty of 0 is easy--everyone gets it right!*

| Method | URL                                | Required Payload     | Action                                                                                   |
| ------ | ---------------------------------- | -------------------- | ---------------------------------------------------------------------------------------- |
| `GET`  | `/all/difficulty`   |        level (easy, medium, or hard)              | Returns a list of riddles of the appropriate difficulty level     |


✔️ **It should return `json` like:**

```json
{
  "difficulty_level": "hard",
 "riddles": [
    {
      "correct": 1,
      "guesses": 44,
      "id": 1,
      "question": "I’m light as a feather, yet the strongest person can’t hold me for five minutes. What am I?",
      "difficulty": 0.9555555555555556
    },
    {
      "correct": 4,
      "guesses": 9,
      "id": 2,
      "question": "What comes down but never goes up?",
      "difficulty": 0.875
    }
 ]
}
```

---

### Like field

What if we want to know which riddles people like? For this, we will have to add allow users to *like* a riddle.

Let's make the `Riddle` keep track of `likes`. You will need to edit `models.py` 

{{< code-action >}} **Let's make the `Riddle` keep track of `likes`. You will need to edit `models.py`**  You will need add a new *field* and write a new *method*.


{{< code-action >}} **Add a new endpoint for you to get all Riddle objects of a category**

| Method | URL                                | Required Payload     | Action                                                                                   |
| ------ | ---------------------------------- | -------------------- | ---------------------------------------------------------------------------------------- |
| `POST`  | `/one/like`   |        id             | Returns a single riddle with the likes  |


```python
{
  "riddle": {
    "id": 1,
    "question": "I’m light as a feather, yet the strongest person can’t hold me for five minutes. What am I?",
    "guesses": 43,
    "correct": 1,
    "likes": 10
  } 
}
```



---

<!-- ### Foreign Key

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

💻 **Try to incorporate a many-to-one relationship in `models.py`.** A few ideas:
- Make the category field it's own Model. Each category can have many songs that belong to it.
- Make the question field its own Model to hold the history of changes
- Make the answer field its own Model to hold the history of changes
 -->


<!-- 
### Interface: Riddle Client 

We will talk more about clients later in this unit, but for now just aquaint yourself with the [Requests library](https://requests.readthedocs.io/en/latest/). 

{{< code-action >}} **Create a new python file:** `client.py`

{{< code-action >}}  **Try to access the public Riddle server, [http://sycs.student.isf.edu.hk/riddle/all](http://sycs.student.isf.edu.hk/riddle/all), using the `Requests` library in this file.**

{{< code-action >}} **A few more things to try:**
- format the response JSON in a user friendly, readable format 
- hit a GET route that requires a payload
- hit a POST route that requires a payload  -->



<!-- 
### Hidden Data 

Organizations often choose to keep data about their models that is not public. 

{{< code-action >}} **Add a new field to the `Riddle` model that tracks how many times that riddle has been accessed.** For example, each time the Riddle queried from `riddle/one`, `riddle/guess`, or `riddle/difficulty` the field will be increased by 1. 

{{< code-action >}} **Now, add a new field to the `Riddle` model that tracks how many times that riddle has been changed.**

🤔 **Be sure to hide these new fields from all your JSON responses.** You may want to write a secret endpoint, that provides all of the secret data. 


--- -->