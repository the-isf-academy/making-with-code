---
title: "5. Client w/AI"
type: lab
draft: true
---

# Client with AI

In this lab you will create a frontend client for your Networking backend project. We will use Gemini to help develop a quick prototype. 

---

## [0] Set Up


{{< code-action "First, clone the repository" >}} in your `unit03_networking` folder.  Be sure to change `yourgithubusername` to your actual Github username.

```shell
cd ~/desktop/making_with_code/unit03_networking/
git clone https://github.com/the-isf-academy/networking_client_ai_yourgithubusername
cd networking_client_ai_yourgithubusername
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

## [1] Using Gemini

Use the structure of this prompt:

```
Can you please create a Python client application using Tkinter. It will interact with an API at this base url: http://sycs.student.isf.edu.hk/riddle

For the payload, be sure to use params with the Requests library. 

Here is the is information on the available endpoints:

{
    "GET /all": {
        "description": "Returns a list of all riddles ",
        "payload": "none"
    },
    "POST /new": {
        "description": "Add a new riddle to the db ",
        "payload": "question: str, answer: str"
    },
    "PUT /guess": {
        "description": "Guess the answer to a riddle with a given id",
        "payload": "id: int, guess: str"
    }
}
```


Here is an example of a helpful prompt to edit specific endpoints.

```
For the guess endpoint, can you please parse the JSON. Please only provide the edited functions.


{

    "correct": false,

    "riddle": {

        "correct_guesses": 9,

        "id": 1,

        "question": "Which letter of the alphabet has the most water?",

        "total_guesses": 31

    }

}```

---

## [2] Improving AI 


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

