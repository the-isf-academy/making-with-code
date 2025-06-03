---
title: "4. Client"
type: lab
draft: true
---

# Client

In this lab we will create a Client in the form of a Command Line Interface(CLI) for the Riddle server. We will use the `Requests` library to send and recieve HTTP requests. To learn more about the `Requests` library, checkout its [documentation](https://requests.readthedocs.io/en/latest/).


---


## [0] What is a client?


Since the riddle server is an API with no user interface, we end up writing a lot of
HTTP requests into the Terminal to use it. What if we had a program which took care
of making these requests for us? A program like this is called a *client*.

**Any app which uses the Internet is a client.**

{{< figure src=https://res.cloudinary.com/lwgatsby/f_auto/www/uploads/2023/05/client-server-network.jpg" width="50%">}}


The client, or app, is constantly making HTTP requests to a server to send and receive information.

---

## [1] Set Up


{{< code-action "Go to the unit folder, clone the riddler server lab, and cd into the repo." >}}
```shell
cd ~/desktop/making_with_code/unit03_networking/
git clone https://github.com/the-isf-academy/lab_client_YOURGITHUBUSERNAME
cd lab_client_YOURGITHUBUSERNAME
```

{{< code-action "Install the requirements." >}}
```shell
poetry install
```

{{< code-action "Enter the poetry shell." >}}
```shell
poetry shell
```

📄 **The repository has the following files.**  In this lab we will just focus on the bolded files.
- **`riddle_client.py`**
- **`test_riddle_client.py`**
- `gui_template.py`
- `gui_view.py`

---

### Riddle API Refresher

🌐 **Visit [http://sycs.student.isf.edu.hk/riddle/all](http://sycs.student.isf.edu.hk/riddle/all) to view riddle server.**

💻 **As a reminder, you can make `GET` and `POST` requests to the API using the `httpie` tool**
```shell
http get http://sycs.student.isf.edu.hk/riddle/all
```

```shell
http post http://sycs.student.isf.edu.hk/riddle/guess id=1 guess="pickles" 
```

Here is a cheatsheet of the Riddle endpoints, what parameters they take in their payload, and what they do:

| Method | URL                                | Required Payload     | Action                                                                                   |
| ------ | ---------------------------------- | -------------------- | ---------------------------------------------------------------------------------------- |
| `GET`  | `/riddle/all`   |                      | Returns a list of all the riddles, without answers.                                      |
| `GET`  | `/riddle/one`   | `id`                 | Returns the riddle if it exists. (Otherwise, it returns an error with status code 404.)  |
| `GET`  | `/riddle/difficulty`   | `id`                 | Returns the riddle if it exists with its difficulty score. (Otherwise, it returns an error with status code 404.)  |
| `POST` | `/riddle/new`   | `question`, `answer` | Creates a new riddle (with an automatically-assigned id). Returns the riddle.            |
| `POST` | `/riddle/guess` | `id`, `guess`        | Checks whether the guess is correct. In the response, `correct` is `True` or `False`.    |

---

### riddle_client.py

The `RiddleClient` class controls the `HTTP requests` to the [Riddle Server](http://sycs.student.isf.edu.hk/riddle/all). It uses the [Requests library](https://requests.readthedocs.io/en/latest/) to send `GET` and `POST` requests. 

It has one properties:

| Property      | Description                                     |
|---------------|-------------------------------------------------|
| **riddle_server** | stores the url of the riddle server             |

And the following methods:

| Method                          | Description                                                          |
|---------------------------------|----------------------------------------------------------------------|
| **view_all_riddles()**              | GETS all of the riddles and prints them as a bulleted list       |
| **guess_riddle(user_chosen_id, user_guess)** | GETS one riddle with the requested ID                            |


--- 

### `all_riddles()`

👀 **First let's look at the method`all_riddles()`** that sends an **HTTP GET** request to the Riddle server endpoint `riddle/all`.

```python {linenos=inline}
def all_riddles(self):
        '''This method sends a GET request to riddle/all.'''

        # stores the full address for /all
        all_riddles_address = self.riddle_server + 'all'

        # makes HTTP GET request 
        response = requests.get(all_riddles_address)

        # checks if request is successful
        if response.status_code == 200:

            # stores the response JSON
            all_riddles_json = response.json()

            parsed_riddle_list = []

            for riddle_dict in all_riddles_json['riddles']:
                parsed_riddle_list.append( f"{riddle_dict['id']}# {riddle_dict['question']}")

            # returns the list of riddles 
            return parsed_riddle_list

        else:     
            # returns HTTP error code, if request is unsuccessful
            return f"HTTP error {response.status_code}"
```
- `line 5:` stores the full URL address of where to get all of the riddles. It uses the `riddle_server` property of the client class as the base address and adds the endpoint to the end of it.
- `line 8:` sends an HTTP GET request to the server and stores the response.
- `lines 11-22:` If the HTTP request was sucessful, it parses the JSON
  - `line 14:` converts the response from the server into JSON.
  - `line 16-22:` returns a list of nicely formmated riddles with the id and question
- `line 12-13`: If the HTTP request was unsuccessful, return the error status code

---

### `guess_riddle()`

👀 **Now, let's look at the method`guess_riddle()`** that sends an **HTTP POST** request to the Riddle server endpoint `riddle/guess`.


```python {linenos=inline}
def guess_riddle(self, user_chosen_id, user_guess):
        '''This method sends a POST request to riddle/guess.'''

        # stores the full address for /guess
        guess_riddles_address = self.riddle_server + 'guess'

        # stores the payload in a dictionary
        payload = {
            'id': user_chosen_id,
            'guess': user_guess
        }

        # makes HTTP POST request with the payload
        response = requests.post(guess_riddles_address, json=payload)

        if response.status_code == 200:
            guess_riddle_json = response.json()

            # parse response JSON
            if 'riddle' in guess_riddle_json:
                parsed_messaged = ""

                if guess_riddle_json['riddle']['correct'] == True:
                    parsed_messaged = 'Correct!!!'

                else:
                    parsed_messaged = 'Incorrect ;('

                return parsed_messaged

            else:
                return guess_riddle_json['error']

        else:
            return f"HTTP error {response.status_code}"
```
- `line 5:` stores the full URL address of where to guess one riddle.
- `lines 8-11:` stores the payload in a dictionary.
- `line 14` sends an HTTP POST request with the payload to the server and stores the response.
- `lines 16-32` If the HTTP request was sucessful, it parses the JSON
  - `line 17` - get the json from the HTTP request
  - `line 21` - creates a variable to store the parsed message
  - `line 22-19` - checks if the guess was correct or incorrect and returns an appropriate message
  - `line 21-32` - returns error JSON
- `line 34-35`: If the HTTP request was unsuccessful, return the error status code

---

## [2] Extend the Client

💻 **Your job is to add 2 methods to the `riddle_client.py`.** 
- `view_one_riddle()`
  - allows the user to input a riddle `id` 
  - if riddle exists, return specific information for the given riddle
  - returns the specific information for the given riddle
- `new_riddle()` 
  - allows the user to input a riddle `question` and `answer`
  - if riddle was added, return a success message 


📄 **For each new functionality, you will need to edit:**
- `riddle_client.py`
- `test_riddle_client.py`


{{< aside "Test File" >}}

✅ Use the test file to check your methods return appropriate message for each use case. 

- is the success message correct? 
- is the error message appropriate? *(try sending a riddle id that does not exist)*
- what if there is an HTTP error? *(try sending incorrect parameters, like a float 3.5 as the id)*

{{< /aside >}}

---

### A few tips


🐞 **Debugging**
- Test, test, test! Make sure you are confident in each piece **before moving on**. 
- Use `print()` statements CONSTANTLY to give yourself more information 
- Copy and Paste are your best friends 

| code            | likely cause                                                       |
|------|--------------------------------------------------------------------|
| **400**   bad request        | your `payload` is formatted incorrectly                            |
| **404**   not found          | wrong `endpoint` <br> *---or---* <br> the riddle doesn't exist                          |
| **405**   method not allowed | you used `POST` instead of `GET` <br> *---or---* <br> you used `GET` instead of `POST` |
---

📚 **Parsing JSON**

The HTTP response is given to us in `JSON`.  

`JSON` is a standardized format to transfer data over a network. It represents data in a key/value pair, just like a Python dictionary.

**You can parse `JSON`, just as you would a [Python dictionary](https://realpython.com/iterate-through-dictionary-python/).**

💡 *What is in the `JSON response` if the guess is correct? If the guess is incorrect?*



---

## [3] Deliverables

{{< deliverables "Once you've successfully completed the client:" >}}  


{{< write-action >}} **Fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSfjuMkLnj7j1NkqclsqiPVVUdrf6ZccRsTUifB6qSbAwenRvQ/viewform?usp=sf_link)**

{{< code-action "Push your code to Github." >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}


---

## [4] Extension

### Explore GUI

Currently when you run `python gui_template.py`, the GUI does not open. 

💻  **Figure out how to start the `RiddlerGUI` when you run `python gui_template.py`**

💻  **Try to customize the GUI by referencing the [CustomTkinter Documentation](https://customtkinter.tomschimansky.com/documentation/).** 
- What are you able to change about the aesthetics of the app? 