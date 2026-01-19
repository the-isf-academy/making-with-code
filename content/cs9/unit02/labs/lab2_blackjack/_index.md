---
title: 3. Blackjack
resources:
# - name: Uno
#   src: images/courses/cs9/unit02/02_01_uno.jpg
draft: true
---

# Blacjack Lab

In this lab, you are going to go behind the scenes of the classic card game, Blackjack.

{{< figure src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e4/BlackJack6.jpg/1200px-BlackJack6.jpg" width="30%" >}}


## [0] Let's Play Uno

🃏 **Let's start by playing the classic card game, Blackjack.** As you're playing, consider the different components and mechanics of the game. 

---

## [0] Setup

{{< code-action "Start by going into your" >}} `unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/unit02_games
```

{{< code-action "Clone your starter code." >}} Be sure to change `YOUR-GITHUB-USERNAME` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab_blackjack_YOUR-GITHUB-USERNAME
```

{{< code-action "cd into the lab" >}}
```shell
cd lab_blackjack_YOUR-GITHUB-USERNAME
```

{{< code-action "Enter the Poetry shell and install the requirements:" >}}
```shell
poetry shell
poetry install
```

This is the largest software package you have encountered and includes the following files:
- `card.py`
- `deck.py`
- `blackjack.py`
- `game.py`
- `view.py`
- `cards.csv`

---

## [2] Card & Deck

**Here is the UML diagram for the `Card` class.** 
- the `__str__()` method decides how a class is represented when printed

{{<mermaid align="left">}}
classDiagram
    class Card {
        +suit: str
        +rank: str
        +__str__() str
    }
{{< /mermaid >}}

**Here is the UML diagram for the `Deck` class.** The `Deck` is mainly composed of instances of the `Card`.

{{<mermaid align="left">}}
classDiagram
    class Deck {
        +cards: [] Card
        +read_cards_from_file(filename: str) []Card
        +add_card(card) Card
        +shuffle_deck() 
        +get_top_card() Card
        +get_num_cards() int
    }
{{< /mermaid >}}


{{< code-action >}}  **Test the `Card` in `card.py` at the bottom of the file in the `if __name == "__main__":` section.** Be sure you understand  each attribute and method. 

```python
if __name__ == "__main__":
    c1 = Card('Hearts',4)
    print(c1)

    # 💻 try making another instance of a Card

    c2 = Card('Spades','Ace')
    print(c2)
```

{{< code-action >}}  **Test the `Deck` in `deck.py` at the bottom of the file in the `if __name == "__main__":` section.** Be sure you understand  each attribute and method. 

```python
if __name__ == "__main__":
    deck1 = Deck('cards.csv')

    # 💻 test the methods

    print(deck1.get_num_cards())
```

## [3] Blackjack 

**Here is the UML diagram for the `Blackjack` class.** 
{{<mermaid align="left">}}

classDiagram
    class Blackjack {
        +deck: Deck
        +hands: dict
        +current_player_index: int
        +deal_n_cards(n: int) [] Card
        +deal_initial_cards()
        +hit(player_index)
        +get_hand_value(player_index) int
        +check_bust(player_index) bool
        +get_player_type() str
        +current_player_hand() [] Card
        +increment_player_num()
        +computer_turn()
        +get_winner() str
        +check_end() bool
    }
{{< /mermaid >}}


{{< code-action >}}  **Test the `Blackjack` in `blackjack.py` at the bottom of the file in the `if __name == "__main__":` section.** Be sure you understand  each attribute and method. 
- Be sure to read the comments to understand the purpose of each method

```python
if __name__ == "__main__":
    blackjack = Blackjack()

    # 💻 experiment with the attributes and methods
    # ensure you understand how the game works

    blackjack.deal_initial_cards()
    for card in blackjack.current_player_hand():
        print(card)

```

## [4] Game Logic


{{< code-action >}} **It's up to you to write the game logic in `game.py` by implementing your flow chart.** You will use the `Blackjack` and `TerminalView` classes.

Functions should include to:
- hit
- stand 
- bust 
- view hand
- view winner

If you're interested, you can find the [rules of Blackjack here](https://www.venetianlasvegas.com/resort/casino/table-games/how-to-play-blackjack.html#:~:text=Blackjack%20Rules&text=The%20object%20of%20the%20game,a%20one%20or%20an%2011.)


{{< code-action >}}  **Test your game as often as possible.**
```shell
python game.py
```

{{< expand "example gameplay output" >}}
```
---------------------------------------------------
-------------------- Blackjack --------------------
--------------------------------------------------- 


... 🔀 Dealing Cards
______________________________________________________________________

👤 0, it is your turn.

 Current hand:
6 of Spades
5 of Spades
?
[move] hit
______________________________________________________________________

👤 0, it is your turn.

 Current hand:
6 of Spades
5 of Spades
10 of Diamonds
?
[move] stand
______________________________________________________________________

👤 1, it is your turn.

 Current hand:
4 of Hearts
2 of Clubs
?
[move] stand
______________________________________________________________________

👤 2, it is your turn.

🥇 Player 0 won!
{{< /expand >}}

> 



---

## [3] Computer Strategy

As you've experienced, you are playing against a computer. At the moment, the computer always hits once as their turn. However, the current computer is not very intelligent. 
  
**Let's make a slightly more competitive computer by considering the best strategy for blackjack.** 


{{< code-action >}} **Write a slightly more competitive computer by changing the `computer_turn()` method in the `Blackjack` class.**

{{< code-action >}} **Test your strategy by playing the game!**

---

## [5] Deliverables

{{< deliverables  >}}

**Once you've successfully completed the game be sure to fill out [this Google form](https://docs.google.com/forms/d/1qNaEZUFNW-930oUOhfmo2ZWatHrMlWcuNBJ59D-El-Y/edit)**.


{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe what you did"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}


---


## [6] Extensions

Ideas include:
- create a Player class
  - player name
  - hand
  - top card 
- betting mechanic 
- ability to always view other player's top card 
