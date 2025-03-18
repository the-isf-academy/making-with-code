---
title: 4. Uno Lab
resources:
- name: Uno
  src: images/courses/cs9/unit02/02_01_uno.jpg
# draft: true
---

# Uno Lab

In this lab, you are construct elements of the classic card game, Uno.

{{< figure src="images/courses/cs9/unit02/02_01_uno.jpg" width="400px" >}}

## [0] Let's Play Uno

🃏 **Let's start by playing the classic card game, Uno.** As you're playing, consider the different components and mechanics of the game. 

{{< checkpoint >}}

{{< write-action >}} **As you play, construct your model for the elements of Uno.**


{{< /checkpoint >}}

---

## [0] Setup

{{< code-action "Start by going into your" >}} `cs9/unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/unit02_games
```

{{< code-action "Clone your starter code." >}} Be sure to change `yourgithubusername` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab_uno_yourgithubusername
```


{{< code-action "Enter the Poetry shell and install the requirements:" >}}
```shell
poetry shell
poetry install
```

This is the largest software package you have encountered and includes the following files:
- `card.py`
- `deck.py`
- `player.py`
- `uno.py`
- `uno_cards.csv`

---

## [2] Implement your Models


{{< code-action >}} **Impelment for model of the `Card`.** Test it to ensure it works as you expect. 

{{< code-action >}} **Impelment for model of the `Deck`** Test it to ensure it works as you expect. 

{{< code-action >}} **Impelment for model of the `Player`** Test it to ensure it works as you expect. 

{{< code-action >}} **Impelment for model of the `Uno`** Test it to ensure it works as you expect. 


## [3] Deliverables

{{< deliverables  >}}

**Once you've successfully completed the game be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSeQKG6s2Z7LpDZHpKG3deH4IiPFg9Uoz8GcyYnN39fornqd3A/viewform?usp=sf_link)**.


{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your drawing and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}

---

## [4] Extension 

{{< code-action >}} **Impelment the game loop for Uno** You will need to create two files:
- `view.py`
- `game.py`





<!-- 
As you've experienced, you are playing against a computer. The `ComputerPlayer` has 3 main methods.
- `get_playable_cards()`
- `play_card()`
- `choose_color()` 

However, the current computer is not very intelligent. 
  
**Let's make a slightly more competitive computer by considering the best strategy for uno.** 

It's up to you to extend the `ComputerPlayer` class and complete the `StrategicComputerPlayer` class:

**You will NEED to override the following methods of `StrategicComputerPlayer` to successfully write a better computer strategy:**
- `get_playable_cards()`
- `choose_color()`
> *a more advanced strategy will also override `play_card()`*

**🤔 Your goal: write a strategic computer that consistently wins more than 35-40% of games against 2 other computer players who are using the basic strategy.** Consider the rules and mechanics of Uno. Given a hand of cards, what would make playing one card better than playing another card? 



{{< code-action >}} **Finish `StrategicComputerPlayer` to implement a strategic strategy.**
> You may want to read more about [inheritance](http://programarcadegames.com/index.php?chapter=introduction_to_classes&lang=en#section_12_6).

{{< code-action >}} **Test your strategy by running:**
```shell
python test_lab.py -k strategy
```
> *if you receive a `raise NotImplementedError`, it is because you have not overridden `get_playable_cards()` AND `choose_color()`*

---


--- -->

<!-- 
## [6] Extension:

Now that you've got a fully functional Uno game, let's expand its functionality. 

It's up to you which extension to work on. If you have your own idea for extending Uno, feel free to work on that!

---

### [More Advanced Strategy]

Can you make your `StrategicComputerPlayer` even more advanced?  You'll need to override the `play_card()` method.

{{< code-action >}} **Make an even more strategic player!** How high can you make the win percentage? It may be helpful to think through hou make the decision of which card to play at which time in the game. 

{{< code-action >}} **Test your strategy by running:**
```shell
python test_lab.py -k strategy
```

---

### [Saying Uno]

Currently, there is no way to system in place for saying 'Uno'. It's up to you to add in that feature!

{{< code-action >}} **Add a 'saying Uno' feature into the game.** Be sure to consider:
- how will you allow the player to say 'Uno'?
- how will you keep track if the player said 'Uno' at the correct time? 
- how will you allow the player to say 'Uno' and play a card? 
- how will you penalize the player if they forget to say 'Uno? 

👾 **Play test your feature to ensure it works as intended!** 
> 🤔 *How would you add in this feature to the `ComputerPlayer`?*
---

### [Advanced Deck Building]

Cards are read into the deck as entries in a csv file. Look at the `deck.py` module and you'll note that we're using pandas to read the cards, looks like those data science skills will come in handy after all!

{{< look-action >}} **Take a look at the current cards in `uno_cards.csv`.** As you can see, each card is on a new line and commas separate their properties. 

{{< code-action >}} **Create your own deck and add a new special card by writing new a csv file.** Just create a new csv file with the name of your special card in the special column.

{{< code-action >}} **Implement your special card in the `UnoGame` class.**

👾 **Play test your new deck to ensure it works as intended!** 




 <!-- Fortunately, [Uno's functionality is well documented](https://cs.fablearn.org/docs/uno/index.html).

- [Game](https://cs.fablearn.org/docs/uno/game.html#game.UnoGame)
- [View](https://cs.fablearn.org/docs/uno/view.html#view.TerminalView)
- [Card](https://cs.fablearn.org/docs/uno/card.html#card.Card)
- [Deck](https://cs.fablearn.org/docs/uno/deck.html#deck.Deck)
- [Player](https://cs.fablearn.org/docs/uno/player.html#player.Player)
    - [HumanPlayer](https://cs.fablearn.org/docs/uno/player.html#player.HumanPlayer)
    - [ComputerPlayer](https://cs.fablearn.org/docs/uno/player.html#player.ComputerPlayer)
        - [RandomComputerPlayer](https://cs.fablearn.org/docs/uno/player.html#player.RandomComputerPlayer)
        - [StudentComputerPlayer](https://cs.fablearn.org/docs/uno/player.html#player.StudentComputerPlayer) --> -->


