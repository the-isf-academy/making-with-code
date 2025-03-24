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

---

### Solutions

{{< expand "Card" >}}
```python
class Card():
    def __init__(self, color, number, special=None):
        
        self.color = color
        self.number = number
        self.special = special

    def __str__(self):  
        if self.special:
            if self.color: 
                return f"{self.color} {self.special}"
            
            else:
                return f"{self.special}"
            
        else:
            return f"{self.color} {self.number}"
```
{{< /expand >}}

{{< expand "Deck" >}}
```python
class Deck():
    def __init__(self, filename=None):
        if filename:
            self.cards = self.read_cards_from_file(filename)
        else:
            self.cards = []
        self.shuffle_deck()

    def read_cards_from_file(self, filename):
        try:
            cards = []
            deckDF = pd.read_csv(filename).fillna('')
            for index, row in deckDF.iterrows():
                cards.append(Card(row.color, row.number, row.special))
            return cards
        except Exception as e:
            print("Exception while reading deck: ", e)

    def add_card(self, card):
        self.cards.append(card)

    def shuffle_deck(self):
        shuffle(self.cards)

    def get_top_card(self):
        return self.cards.pop()  

    def get_num_cards(self):
        return len(self.cards)
```
{{< /expand >}}

{{< expand "Player" >}}
```python
class Player():
    def __init__(self, name):
        self.name = name
        self.hand = []
        
    def add_to_hand(self, card):
        self.hand.append(card)

    def play_card(self,card):
        card_index = self.hand.index(card)
        chosen_card = self.hand[card_index]
        self.hand.remove(chosen_card)
        return card

    def get_hand(self):
        hand_for_view = []
        for card in self.hand:
            hand_for_view.append(str(card))

        return hand_for_view 
    
    def choose_color(self):
        return choice(['Red','Blue','Green','Blue'])

    def check_win(self):
        return len(self.hand) == 0
```
{{< /expand >}}

{{< expand "Uno" >}}
```python
# class for Uno game
# =============================================================================


from deck import Deck
from player import Player
from random import choice

class Uno():
    def __init__(self, deck_file=None, human_name_list = None):
        self.deck = Deck(deck_file)
        self.discard = Deck()
        self.direction = 1
        self.top_card = self.deal_n_cards(1)[0]

        if "wild" in self.top_card.special:
            self.top_card.color = choice(["red", "blue", "green", "yellow"])

        self.current_player_index = 0
        self.top_card = self.deal_n_cards(1)[0]

        self.players = []

        for name in human_name_list:
            self.players.append(Player(name))

    def deal_starting_cards(self):
        for i in range(7):
            for player in self.players:
                self.deal_n_cards(1,player)

    def deal_n_cards(self, n, player=None):
        cards = []
        for i in range(n):
            if self.deck.get_num_cards() == 0:
                if self.discard.get_num_cards() == 0:
                    return None
                
                self.discard.shuffle_deck()
                empty_deck = self.deck
                self.deck = self.discard
                self.discard = empty_deck

            card = self.deck.get_top_card()
            cards.append(card)
            
            if player:
                player.add_to_hand(card)

        return cards
    
    def increment_player_num(self):
        self.current_player_index = (self.current_player_index + self.direction) % len(self.players)

    def get_current_player(self):
        return self.players[self.current_player_index]
    
    def get_next_player(self):
        next_player_index = (self.current_player_index + self.direction) % len(self.players)
        return self.players[next_player_index]
    
    def play_valid_card(self, player_card):
        self.discard.add_card(self.top_card)
        self.top_card = player_card

    def check_if_card_valid(self, card):
        # 💻 You must finish this method yourself  

        return 
    
    def special_card_action(self, card):
        # 💻 You must finish this method yourself  

        if card.special == 'wild':
            new_color = self.current_player().choose_color()
            self.top_card.color = new_color


        
if __name__ == "__main__":
    print ("--- testing Uno features ---")

    uno = Uno("uno_cards.csv", ["P1", "P2"])
    uno.deal_starting_cards()

    print("\n -- get_current_player() --")
    print(uno.get_current_player(), uno.get_current_player().get_hand())

    # 💻 test all of the features
```
{{< /expand >}}

💻 **For `Uno()` you must finish `check_if_card_valid()` and `special_card_action()`** Be sure to test all of the methods at the bottom of the file.


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
        - [StudentComputerPlayer](https://cs.fablearn.org/docs/uno/player.html#player.StudentComputerPlayer) --> 

