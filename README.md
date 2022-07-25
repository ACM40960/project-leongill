<p align="left"><img width=50% src="https://github.com/ACM40960/project-leongill/blob/main/README.GIF"></p>


# Using The Model
The model employs three classes which are deck, dealer and player.

### Deck 
A deck object is initialised as:
```R
test_deck = deck(n) #n is the number of full decks making up the deck
```
The deck is shuffled when initialized. The deck can has two methods which allow for specified cards to be removed and for a random card to be drawn and returned:
```python
test_deck.remove("2")#If the deck has > 1 "2" card, it is removed.
test_deck.draw()#Returns the randomly removed card
test_deck.show()
```

### Player
The player object is initialised as:
```python
test_player = player() 
```
This player has an empty hand attribute. The player can draw if given a card as input, 
```python
test_player.draw(test_deck)#Adds t
```
