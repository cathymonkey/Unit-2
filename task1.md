### Task 3:

Situation: 
In a game of guessing a number between 1-100 for two players, player A and player B. 
The player A knows the number. 
The player B is trying to guess with the least number of attempts.
Player A can only reply to a guess from the other player B with “low”, “high”, or “That is the number”.

Your task is to create a computer program for Player B. 

## Codes:
```.py
import random
player_A_number = random.randrange(1,100,1)
print("The number of player A is {}".format(player_A_number))



while True:
    player_B_guess_number = int(input("Player B, please input 1 integer between 1~100 to see if"
                                      "it is player A's secret number:"))

    if player_B_guess_number > player_A_number:
        print("High")

    if player_B_guess_number < player_A_number:
        print("Low")

    if player_B_guess_number == player_A_number:
        print("That is the number")
        break

````
