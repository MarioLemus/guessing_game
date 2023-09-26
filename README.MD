# Guessing game

The purpose of this app is to make the guessing game funny enough to take some of your time playing it

## structure

(all this clases follows the single responsability)

IO

- input
- output

- verify_input_into_limits # the user number is between 1 and x

GameState(singleton)

- P1 = PLAYER 1
- P2 = PLAYER 2
- winner = nil
- current_player = P1
- current_round = 1

- change_current_player # check current_player to toggle for new Player
- change_current_round # current guesing cycle (a round is finished when the 2 players guess and none guess, or when there is a winner)
- declare_winner(player) # change winner from nil to the current_player, notify, quit game

<!--->
IGuessingGame (follows dependency inversion, is correct if flexibility is not super required, otherwise is better to implement interface segregation principle)

- generate
- reset
<--->
THIS CODE BELLOW FOLLOWS THE INTERFACE SEGREGATION PRINCIPLE (more flexible way of structuring)

IGenerable

- generate

IResetable

- reset

GuessTheCard
**include IGenerable**
**include IResetable**

GuessTheNumber
**include IGenerable**
**include IResetable**

GuessingGame

- if game == guess_cards
- **include GuessTheCard**
- if game == guess_number
- **include GuessTheNumber**
- you can implement whatever other game, while it follows the contract restrictions
