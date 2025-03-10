---
title: 1. Pet Lab
# draft: true
---

# Pet Lab



👀 **In this lab, you will learn about object oriented programming.** You will create a pet simulator game.

---

## [0] Setup
{{< code-action "Start by going into your" >}} `unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/unit02_games
```

{{< code-action "Then, clone your starter code." >}} Be sure to change `YOUR-GITHUB-USERNAME` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab_pet_YOUR-GITHUB-USERNAME
cd lab_pet_YOUR-GITHUB-USERNAME
```

{{< code-action "Enter the Poetry shell and install the requirements:" >}}
```shell
poetry shell
poetry install
```

{{< code-action >}} `cd` **into the lab**
```shell
cd lab_pet_YOUR-GITHUB-USERNAME
```


{{< code-action "Enter the Poetry Shell and install the required packages." >}} *Each line should go one at a time.*
```shell
poetry shell
poetry install
```


This lab includes the following files:
- `pet.py`
- `game_interface.py`
- `helpers.py`

---

## [1] Building your Pet

{{< code-action  >}} **Open the folder in VSCode and open `pet.py`.** We will first focus on the the `Pet()` Python class.
```shell
code .
```

{{<mermaid align="left">}}
classDiagram
    class SpellingBee {
        + name: str
        + bored: [] boolean
        + introduce() 
        + play() 
    }
{{< /mermaid >}}

The `Pet` has the following attributes:
- `name`
- `bored`

and the following methods:
- `introduce()`
- `play()` 


{{< code-action >}} **Let's start by running `pet.py`** 
> *Do not copy `$`, simply type the command after the `$`. It is to distinguish between Terminal commands v. Terminal output.*
```shell
$ python pet.py
-- testing Pet -- 
Peanut
```

{{< code-action >}}  **Test the other `attributes` and `methods` code at the bottom of the file in the `if __name == "__main__":` section and run `python pet.py`.** This section is only called when file is ran, not when the file is imported.

```python
if __name__ == "__main__":
    print('-- testing Pet -- ')

    pet1 = Pet()                # create an instance of a Pet
    pet1.set_name("Peanut")     # call `set_name()` method
    print(pet1.name)    
```

{{< code-action >}} **Test each of the attributes and methods in `pet.py`.** When you run `python _pet.py` it should look something like this:
```shell
$ python test_pet.py
-- testing Pet -- 
Peanut
👋 Hi, I am Peanut!
Wooooo, running!
True
```


---

## [2] What type of animal is your pet?

Now that you've used the `Pet` class, let's delve into the code and make our `Pet` more complex. People can have all different types of pets, so **lets' add a `species` attribute** to our `Pet`.

{{< aside >}}
This section of the lab walks you through how to write a `class` in Python. Keep a look out for the {{< code-action  >}} to ensure you add all the necessary features. 
{{< /aside >}}

👀 **Go to `pet.py` in VSCode**

---

### What's a class?

In the `test_pet.py`, **you just successfully used an instance of a class!**

{{< look-action >}} If you look in the Pet class, you can see on `line 1` - that we name the class `Pet`. **A class a simply a blueprint for group of data, or information, with specific functionalities.** In this class we are creating a blueprint for storing information about pets. 

```python {linenos=table, hl_lines=["1"],linenostart=1}
class Pet:
    def __init__(self):
        '''This initializes the pet with its attributes.'''

        self.name = None            # stores the pet's name as a string
        self.bored = False          # stores if the pet is bored
```

---

### Adding a new attribute

{{< look-action >}} The information associated with a `Pet` is defined on `lines 5-7`. **Information associated with a class is called `attribute` and is stored in a variable.** Our pet has three attributes. attributes are variables that only belong to a specific class.

```python {linenos=table, hl_lines=["5-6"],linenostart=3}
class Pet:
    def __init__(self):
        '''This initializes the pet with its attributes.'''

        self.name = None            # stores the pet's name as a string
        self.bored = False          # stores if the pet is bored
```
>The `Pet` currently two attributes, `name` and `bored`.


{{< code-action  >}} **Add a `species` attribute to the `Pet` class that is initially set to `None`.** It will work just like the `name` attribute.

---

### Adding a new method

Now that we've added the `species` attribute, we need to add a method to set the attribute.

{{< look-action >}} If you scroll down to lines 9-12, we see an example of a method. **A method is similar to a function. The only difference is that a method belongs to a certain class, like `Pet`.**


```python {linenos=table, linenostart=10}
def set_name(self, name):
    '''This method sets the name attribute'''

    self.name = name
```
> The `set_name()` method changes the `name` attribute to whatever the user put as the parameter.
>
> *e.g. `my_pet.set_name('Bob')`*

Just like the `name` attribute, we need to be able to set the `species` of our pet.

{{< code-action "Add a new method called " >}} **`set_species()`.** This method should change the `species` attribute of the `Pet` class.

---

### Testing your changes

Let's see if the `species` attribute and `set_species()` method is working by jumping back into `test_pet.py`.

{{< code-action  >}} **Test your changes by using `set_species()` on `pet1`**
```shell
$ python test_pet.py
Peanut
👋 Hi, I am Peanut!
Wooooo, running!
True
Dog
```

---

### Using the species attribute

Right now, the `introduce()` method just has the pet say their name. Let's make it more detailed by including their `species` in the introduction.

```python {linenos=table, linenostart=14}
def introduce(self):
  '''This method introduces the pet with its name.'''

  print(f"👋 Hi, I am {self.name}!")
```
<br>

{{< code-action  >}} **Edit the `introduce()` method so that your pet will also tell you its species.**

{{< code-action  >}} **Test the updated `introduce()` method in `test_pet.py`.** 
```shell
$ python test_pet.py
Peanut
👋 Hi, I am Peanut and I am a dog!
Wooooo, running!
True
Dog
```
---



## [3] Pet Simulator


👾 **Now that you have experienced the backend of the `Pet`, let's play the game!** The `Pet` now has a nice Terminal interface where you can interact with it through a menu system, just like a lo-fi text-based video game.
```shell
python game_interface.py
```




```shell
-----------------------------------
---- Welcome to Pet Simulator ----
----------------------------------- 

What would you like to name your pet?
 > Peanut
-------------------------
Your pet is ready!
-------------------------
> Introduce                                                                                                                
  Quit         
```

---

### Add play()

{{< code-action >}} **Edit `game_interface.py` so you can `play()` with your `Pet`!** Start by reading through the code to make sure you understand how it works. Then make small edits to add in `play()`. Be sure to look for:
- how are menu options being displayed? 
- how are the different functions being ran based on the user selection? 

{{< code-action >}} **Play test it!** `python game_interface.py`

---


### Add tired feature

💤 Pet's get tired, just like humans!

{{< code-action >}} **Add the ability to track if the `Pet` is tired.** If it's tired, it should take a `nap()`.
- What attribute will you add? 
- What method will you add?

{{< code-action >}} **Edit `game_interface.py` so you can tell your `Pet` to `nap()`!**

🎮 **Play test it!** `python game_interface.py`


---

## [4] Deliverables


{{< deliverables  >}}

**Once you've successfully completed the game be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLScNmW50atI6K0loMjLd3K03X7esmJqCZZBE1e2qkguzIPP06g/viewform?usp=sf_link)**.


{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your drawing and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}

---

## [5] Extension

{{< aside >}}
If you have your own ideas, build on the `Pet` however you would like! 

But if you're unsure where to start, there are a few ideas below. 
{{< /aside >}}

### Add a hunger level

At this point, you have a working `Pet`, but it's pretty basic. Most pets, get hungry and need to eat. 

**This will require you to add a `hunger` attribute and `eat()` method.**

**Your `hunger` attribute should:**
- be an numerical data type
- decreased when it plays 
- increase when it uses `eat()`

{{< code-action >}} **Test your edits with the `test_pet.py` or `python shell`.**  

{{< code-action >}} **Edit `game_interface.py` to include the new hunger features of the `Pet`**

{{< code-action >}} **Play test it:** `python game_interface.py`

---

### Tamagotchi Features

This lab was inspired by the Tamagotchi!

{{< figure src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f2/Tamagotchi_0124_ubt.jpeg/330px-Tamagotchi_0124_ubt.jpeg" width="40%" >}}

{{< code-action >}} **Include as many of the original Tamagotchi features as you can: [Tamagotchi wiki.](https://en.wikipedia.org/wiki/Tamagotchi!)**     

For example:
- happiness 
- sickness 
- life cycle (baby, child, teen, adult)

---

### Customize the look of your game

{{< code-action >}} **Experiment with the [Colorama Library](https://pypi.org/project/colorama/) to implement colors into your Terminal interface**

---

### Inheritance

{{< code-action >}} **Create subclasses of your `Pet` using `inheritance`.** For example, 
what features do dogs have that cats do not have? 

📖 You'll need to learn how to incorporate inheritance: [12.6 Inheritance](http://programarcadegames.com/index.php?chapter=introduction_to_classes&lang=en#section_12_6)