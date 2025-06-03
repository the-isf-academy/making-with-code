---
title: "4. API"
type: lab
slug: lab_riddle_server
draft: false
---

# Lab API

In this lab we are going to learn how the riddle server is made using Banjo.

## [0] Experience the ISF Riddle Server

The last time we saw riddles, they existed only within each of your computers. You had to manually add new ones and there was no way to keep track of how many people guessed them.

We are now going to look at Riddles that are hosted on the internet!

{{< code-action >}} **Visit [http://sycs.student.isf.edu.hk/riddle/all](http://sycs.student.isf.edu.hk/riddle/all) to view riddle server.**
> Not very easy to read, right? You can install the [JSON Formatter](https://chrome.google.com/webstore/detail/json-formatter/bcjindcccaagfpapjjmafapmmgkkhgoa?hl=en) Chrome extension to view better formatted JSON.*

{{< code-action >}} **Now try making `GET` request to `http://sycs.student.isf.edu.hk/riddle/all` receive the same information using : [httpie.io/app](https://httpie.io/app)**


{{< figure src="images/courses/cs10/unit00/02_banjo_05.png" alt-text="databases" >}}



{{< code-action >}} **Do you know the answer? Try sending a `POST` request to make a guess.** This request to a different url `endpoint`: `/guess`

0. Add a new request
0. Change `GET` to `POST`
0. Paste in the URL: `http://sycs.student.isf.edu.hk/riddle/guess`
0. Select `Body`
0. At the bottom, change `None` to `Form`
0. Add the *payloads:* `id` and `guess`

{{< figure src="images/courses/cs10/unit00/02_banjo_03.png" alt-text="databases" >}}

> **It is common for `POST` requests to send a *payload* with the request.** In this case, the payloads are:
> - `id` specifying which riddle we are guessing
> - `guess` specifying the guess
> We are also sending this request to a different url `endpoint`: `/guess`



---

### Explore the Endpoints

**🔗 Server APIs often rely on different URL *endpoints* to the *base url* to determine what the API should do.**
- The base url to this server is: `http://sycs.student.isf.edu.hk/riddle`

Here is a cheatsheet of the Riddle endpoints, what parameters they take in their payload, and what they do:

| Method | URL                                | Required Payload     | Action                                                                                   |
| ------ | ---------------------------------- | -------------------- | ---------------------------------------------------------------------------------------- |
| `GET`  | `/all`   |                      | Returns a list of all the riddles, without answers.                                      |
| `GET`  | `/one`   | `id`                 | Returns the riddle if it exists |
| `POST` | `/new`   | `question`, `answer` | Creates a new riddle (with an automatically-assigned id). Returns the riddle.            |
| `POST` | `/guess` | `id`, `guess`        | Checks whether the guess is correct. In the response, `correct` is `True` or `False`.    |
| `GET`  | `/difficulty`   | `id`                 | Returns the riddle if it exists with its difficulty score. (Otherwise, it returns an error with status code 404.)  |



{{< checkpoint >}}

{{< code-action "Explore each endpoint in the `httpie tool`, and be sure to successfully:" >}}
- view all riddles without the answers
- view a single riddle
- add a new riddle
- guess a riddle
- try to break the riddle server, what happens when you provide incorrect parameters?

📖 **When using the the httpie tool,**
- for a `GET` request, put the *payload* in the `Params`
- for a `POST` request, put the *payload* in the `Body` > `Form`
{{< /checkpoint >}}


---

## [1] Set Up

{{< code-action "Download Mac app of HTTPIE:" >}} [ httpie.io/download](https://httpie.io/download). We need to download the app to make local HTTP requests for testing purposes.

{{< figure src="https://httpie.io/Images/download-shape.svg" width="25%">}}


{{< code-action "Start by going into the unit folder and the lab." >}} Remember to replace `yourgithubusername` with your actual GitHub username.
```shell
cd ~/desktop/making_with_code/unit03_networking/
cd lab_api_yourgithubusername
```

{{< code-action "Install libraries" >}}
```shell
poetry install
```

{{< code-action "Enter the Poetry shell" >}}
```shell
poetry shell
```

**This server is written using the [Flask Library](https://flask.palletsprojects.com/en/stable/)**. It allows easily write an API to interact with a SQL databse. 

📁 **Our API has a few main files `api.py` `helpers.py`.** 
- `api.py` - API strucutre where endpoints are defined 
- `helpers.py` - helper functions to interact with database
- `database.db` - riddles SQL database

---
## [2] Local Riddle Server

Your computer can host a `local server` that accessess the `riddle API`.


{{< code-action "Now, let's start your local server:" >}} `python api.py`. This will run a local server that is only accessible on your local computer. 


💻 **You can now visit this server in your web browser, just as you did with the riddler server hosted on the internet:**  [127.0.0.1:8000/riddle/all](http://127.0.0.1:8000/riddle/all)

💻 **Open the `HTTPie` desktop app to send the same `GET` request to `/all`.**

{{< figure src="images/courses/cs10/unit00/banjo_server_00.png" width=50%" >}}


{{< look-action " Look at the Terminal window running the server. Notice how it recorded your request." >}}
```shell
[16/Sep/2024 02:44:20] "GET /riddle/all HTTP/1.1" 200 1069
```

---

### Hitting the Server

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
- `/riddle`
- `/riddle/all`
- `/riddle/new`

{{< checkpoint >}}

{{< code-action "Explore both endpoints via the HTTPie desktop app and be sure to successfully:" >}}
- view all riddles without the answers
- create a new riddle
{{< /checkpoint >}}

---

## [3] Writing Routes

In this lab, you will build out the functionality of the Riddle server. Currently, your file only has `riddle/all` and `riddle/new`. 

**It is up to you to add the following endpoints:**
- `riddle/one`
- `riddle/random`
- `riddle/guess`

{{< code-action "Start by opening up the folder:" >}} `code .`
> You should first, open a new terminal tab with `⌘ + T`, so you can keep your server running in one tab, and use the other tab to access your filesystem


{{< code-action >}} **Open the `api.py` file.** Here is where you will write the additional endpoints. 

👀 **First, take a look at the `index()` function.**
```python {linenos=table}
@app.route('/', methods=['GET'])
def index():
    son = {'message': 'Hello from the ISF Riddles API!'}
    return json, 200
```
- `line 1` - defines the URL route and the HTTP request type
- `line 2` - defines a function and any necessary parameters
- `line 3` - defines the JSON response
- `line 4` - returns the JSON and the HTTP response code 

### HTTP response codes

The important HTTP success response codes
- `200` - successful GET or PUT request
- `201` - successful POST request

---

### riddle/one

{{< code-action >}} **Write the `riddle/one` endpoint.** 
- **HTTP method:** `get`
- **Payload/args:** `id`
- **Return:** a single `Riddle` with the `question`, `guesses`, and `correct` properties


🤔 *Which `functions` in `helpers.py`` could be useful?*

{{< checkpoint >}}

💻 **Test the `riddle/one` endpoint in the `HTTPie desktop app`**

```shell
http://127.0.0.1:8000/riddle/one id=4
```


✔️ **It should return `json` like:**

```json
{
  "riddle": {
    "id": 1,
    "question": "I’m light as a feather, yet the strongest person can’t hold me for five minutes. What am I?",
    "total_guesses": 43,
    "correct_guesses": 0  } 
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
    "correct_guesses": 0,
    "difficulty": 0,
    "id": 219,
    "question": "What is full of holes, but can still hold a lot of water?",
    "total_guesses": 0
}

```

{{< /checkpoint >}}

---

### riddle/guess

{{< code-action >}} **Write the `riddle/guess` endpoint.** 
- **HTTP method:**  `put`
- **Payload/args:**  `id` and `guess`
- **Return:** 
  - if the guess was correct
    - message telling the user they were correct
    - a single `Riddle` with all of row values
  - if the guess was incorrect
    - message telling the user they were incorrect
    - a single `Riddle` without the answer

🤔 *Which `functions` in `helpers.py`` could be useful?*

{{< checkpoint >}}

💻 **Test the `riddle/guess` endpoint in the `HTTPie desktop app`**

```shell
http://127.0.0.1:8000/riddle/guess
```

✔️ **It should return `json` like:**

```json
{
    "correct": true,
    "riddle": {
        "answer": "Noon",
        "correct_guesses": 14,
        "difficulty": 0.8235294117647058,
        "id": 3,
        "question": "What time of day, when written in a capital letters, is the same forwards, backwards and upside down?",
        "total_guesses": 17
    }
}

```
{{< /checkpoint >}}


---


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

### Error Messaging

Try to access a riddle that does not exist. You get an error, correct? A better solution is to return an error message with helpful information.

The HTTP code for an erorr is `404`. You are probably familiar with this from surfing the web.

Here is an example of an error message:

```python
if riddle is None:
      return {'error': 'Post not found'}, 404
```  

```python
if not question or not answer:
    return {'error': 'Question and Answer are required.'}, 400
```

Incorporate approprate error messages for each of your endpoints. Try to break them.

The important HTTP success response codes
- `400` - incorrect payload
- `404` - no results found

---

### Difficulty

Since that we track `difficulty`, it would be nice if we could `GET` a list of riddles of `easy`, `medium,` or `hard` difficulty. 

{{< code-action >}} **Write a function `get_riddles_difficulty(level)` that returns all of the riddles within the appropriate range.** 
- reference [SQL WHERE operators](https://www.w3schools.com/sql/sql_where.asp)
- consider what the difficulty ranges should be for easy, medium, hard (difficulty of 1 is impossibly hard, while a Riddle with a difficulty of 0 is easy)

{{< code-action >}} **Write an endpoint returns riddles within a difficulty category** 
- **HTTP method:**  `GET`
- **Payload/args:**  `level` 
- **Return:** 
  - a list of `Riddles` with the `id`, `question`,  `correct`, and `guess` properties of the designated difficulty level

You can use an url parameter like:
```python
@app.route(f'/{BASE_URL}/all/<str:difficulty>', methods=['GET'])
def all_riddles_difficulty(difficulty):
```


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

