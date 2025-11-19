---
title: "5. Client w/AI"
type: lab
# draft: true
---

# Client with AI

In this lab you will create a frontend client for your Networking backend project. We will use Gemini to help develop a quick prototype. 

---

## [0] Set Up


{{< code-action "First, clone the repository" >}} in your `unit03_networking` folder.  Be sure to change `yourgithubusername` to your actual Github username.

```shell
cd ~/desktop/making_with_code/unit03_networking/
git clone https://github.com/the-isf-academy/client_ai_yourgithubusername
cd client_ai_yourgithubusername
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

## [1] Understanding AI Code 

Our goal is to create a GUI for a riddle guessing game that accesses the riddle server at [http://sycs.student.isf.edu.hk/riddle](http://sycs.student.isf.edu.hk/riddle).

**Your goal is to create a GUI to interact with the Riddle server.** It should look similar to this with all buttons working as expected:

{{< figure src="images/courses/cs10/unit00/clientai_0.png" alt-text="databases" width=50% >}}

🤖 **In [Gemimi](http://gemini.google.com/) write a prompt to create a GUI.** You may use the suggestion prompt below or write your own prompt.

```md
Can you please create a Python client application using Tkinter. It will interact with an API at this base url: http://sycs.student.isf.edu.hk/riddle

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



{{< code-action >}} **Copy & Paste the entirety of the AI generated code into `client_ai.py`.** 

{{< code-action >}} **Run `client_ai.py` to test it.** 

{{< checkpoint >}}

Were you successful? Why or why not? 

If you were successful, 
- did you tweak the code?
- did you tweak the prompt?

{{< /checkpoint >}}

---

### Improving the prompt

🤔 **If you were unsuccessful, can you figure out which function is causing the error?** 

🤖 **Improve the prompt by instructing Gemimi to use a specific function that will fix the bug.** Take a peak at the suggested prompt if you need a hint. Feel free to include additional suggestions of certain function not to use to make the code more readable for you.  


{{< expand "Suggested Addition" >}}
```md
For the Requests library, be sure to only use params=payload. 
```
{{< /expand >}}




{{< code-action >}} **Copy & Paste the entirety of the new AI generated code into `client_ai.py`.** 

{{< code-action >}} **Run `client_ai.py` to test it.** 


{{< checkpoint >}}

A few questions to consider:
- Did the improved prompt result in a GUI that works immediately? Why might this be? 
- If the improved prompt did not generate a working GUI, why might it have failed? 
- How would you assess the AI code? 

{{< /checkpoint >}}

--- 

### Improving the GUI

Hopefully by now your GUI works and displays information! However, it is probably still formatted as JSON. Ideally, our GUI should be **parsed**, ensuring it is easy to read. Data parsing is converting raw, unstructured into a more readable format.

{{< figure src="images/courses/cs10/unit00/clientai_1.png" alt-text="databases" width=50% >}}

{{< code-action >}} **Either use targeted AI prompts to fix the formatting OR parse the JSON yourself.** Use the helpful prompt below or experiment on your own. 

{{< expand "Helpful prompt" >}}

Here is an example of a helpful prompt to edit specific endpoints.

```md
For the get_all_riddles() function, please parse the json response. Here is an excerpt of it:

{

    "riddles": [

        {

            "correct_guesses": 11,

            "id": 1,

            "question": "Which letter of the alphabet has the most water?",

            "total_guesses": 34

        },
```

{{< /expand >}}

**Here is an example of parsed JSON**
{{< figure src="images/courses/cs10/unit00/clientai_2.png" alt-text="databases" width=50% >}}

{{< code-action >}} **Ensure each function in your GUI includes easy to read, parses JSON**


{{< checkpoint >}}

A few questions to consider:
- Do you like or dislike the AI parsing? 
- What are advantages and disadvantages to using AI for data parsing? 

{{< /checkpoint >}}

---

## [2] Deliverables


{{< deliverables >}}  

**Once you've successfully completed the worksheet be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSdY-ClGHF5icxgjS4f68p5-eSRlaCRTqR2_x6q-1CmY0d449Q/viewform?usp=publish-editor).**

{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}

---


---

## [3] Extension: Creating a Game

Let's consider alternate clients to interact with the Riddle server, such as a game. 

🤖 **Use AI to generate code a client that functions as a riddle guessing game.** Your game must include the following features:
- the user gets 10 guesses of random riddles from the server 
- the user can input a guess for each riddle
- display to the user if their guess was correct or incorrect 
- after the user has guessed 10 questions, display their total score 

**Here is a Game Client example. As long as it includes the required features, it can look however you'd like.**

---
