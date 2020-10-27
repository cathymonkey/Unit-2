## Task 3:

Situation: 
In a game of guessing a number between 1-100 for two players, player A and player B. 
The player A knows the number. 
The player B is trying to guess with the least number of attempts.
Player A can only reply to a guess from the other player B with “low”, “high”, or “That is the number”.

Your task is to create a computer program for Player B. 

### Codes:

-AI program that will guess the number for Player B:
(Version 1)
```.py
import random
#guess the first number of player A
guess_number_of_player_B = random.randrange(1,100,1)
print("Is your your number {}, player A?".format(guess_number_of_player_B))



while True:

    player_A_reply = input("Please type 'Low', 'High', or 'That is the number' to tell me if I "
                           "guessed the right number or so that I could keep guessing your number: ")
    #generate 3 random variable to guess in a more lucky way.
    random_num_1 = random.randrange(10,20,1)
    random_num_2 = random.randrange(1,9,1)
    random_num_3 = random.randrange(1,4,1)
    #increase and decrease the guess number randomly to bring a more accurate guess
    if player_A_reply == "Low":
        guess_number_of_player_B += random_num_1 + random_num_2 + random_num_3
        print("Is this your number {}, player A?".format(guess_number_of_player_B))

    if player_A_reply == "High":
        guess_number_of_player_B -= random_num_1 - random_num_2 - random_num_3
        print("Is this your number {}, player A?".format(guess_number_of_player_B))

    if player_A_reply == "That is the number":
        print("Yay! I guessed the right number:)")
        break

```

(Version2):
```.py

import random

guess_number_of_player_B = random.randrange(1,100,1)
print("Is your your number {}, player A?".format(guess_number_of_player_B))



while True:

    player_A_reply = input("Please type 'Low', 'High', or 'That is the number' to tell me if I "
                           "guessed the right number or so that I could keep guessing your number: ")

    random_num_1 = random.randrange(10,20,1)
    random_num_2 = random.randrange(1,9,1)
    random_num_3 = random.randrange(1,4,1)
    random_num_4 = random.randrange(0,1,1)

    if player_A_reply == "Low":
        guess_number_of_player_B += random_num_1 + random_num_2 + random_num_3 + random_num_4
        print("Is this your number {}, player A?".format(guess_number_of_player_B))

    if player_A_reply == "High":
        guess_number_of_player_B -= random_num_1 - random_num_2 - random_num_3 -random_num_4
        print("Is this your number {}, player A?".format(guess_number_of_player_B))

    if player_A_reply == "That is the number":
        print("Yay! I guessed the right number:)")
        break

```

(Version 3):

```.py

import random

guess_number_of_player_B = 50
print("Is your your number {}, player A?".format(guess_number_of_player_B))

player_A_reply = input("Please type 'Low', 'High', or 'That is the number' to tell me if I "
                           "guessed the right number or so that I could keep guessing your number: ")


random87_high = random.randrange(75,87,1)
random87_low = random.randrange(87, 100, 1)
random63_high = random.randrange(50, 63, 1)
random63_low = random.randrange(63, 87,1)
random37_high = random.randrange(25, 37,1 )
random37_low = random.randrange(37, 50, 1)
random13_high = random.randrange(1, 13, 1)
random13_low = random.randrange(13,25,1)

if player_A_reply == "Low":
    print("Is your number 75?")
    player_A_reply = input("Please type 'Low', 'High', or 'That is the number' to tell me if I "
                           "guessed the right number or so that I could keep guessing your number: ")
    if player_A_reply == "Low":
        print("Is your number 87?")
        while True:
            player_A_reply = input("Please type 'Low', 'High', or 'That is the number' to tell me if I "
                                   "guessed the right number or so that I could keep guessing your number: ")
            if player_A_reply == "Low":
                while True:
                    random87_low = random.randrange(87, 100, 1)
                    print("Is this your number {}, player A?".format(random87_low))
                    player_A_reply = input("Please type 'Low', 'High', or 'That is the number' to tell me if I "
                                           "guessed the right number or so that I could keep guessing your number: ")
                    if player_A_reply == "That is the number":
                        print("Yay! I guessed the right number:)")
                        break

            if player_A_reply == "High":
                while True:
                    random87_high = random.randrange(75,87,1)
                    print("Is this your number {}, player A?".format(random87_high))
                    player_A_reply = input("Please type 'Low', 'High', or 'That is the number' to tell me if I "
                                           "guessed the right number or so that I could keep guessing your number: ")
                    if player_A_reply == "That is the number":
                        print("Yay! I guessed the right number:)")
                        break

            if player_A_reply == "That is the number":
                print("Yay! I guessed the right number:)")
                break

    elif player_A_reply == "High":
        print("Is your number 63?")
        while True:
            player_A_reply = input("Please type 'Low', 'High', or 'That is the number' to tell me if I "
                                   "guessed the right number or so that I could keep guessing your number: ")
            if player_A_reply == "Low":
                while True:
                    random63_low = random.randrange(63, 87,1)
                    print("Is this your number {}, player A?".format(random63_low))
                    player_A_reply = input("Please type 'Low', 'High', or 'That is the number' to tell me if I "
                                           "guessed the right number or so that I could keep guessing your number: ")
                    if player_A_reply == "That is the number":
                        print("Yay! I guessed the right number:)")
                        break

            if player_A_reply == "High":
                while True:
                    random63_high = random.randrange(50, 63, 1)
                    print("Is this your number {}, player A?".format(random63_high))
                    player_A_reply = input("Please type 'Low', 'High', or 'That is the number' to tell me if I "
                                           "guessed the right number or so that I could keep guessing your number: ")
                    if player_A_reply == "That is the number":
                        print("Yay! I guessed the right number:)")
                        break

            if player_A_reply == "That is the number":
                print("Yay! I guessed the right number:)")
                break

    elif player_A_reply == "That is the number":
        print("Yay! I guessed the right number:)")

elif player_A_reply == "High":
    print("Is your number 25?")
    player_A_reply = input("Please type 'Low', 'High', or 'That is the number' to tell me if I "
                           "guessed the right number or so that I could keep guessing your number: ")
    if player_A_reply == "Low":
        print("Is your number 37?")
        while True:
            player_A_reply = input("Please type 'Low', 'High', or 'That is the number' to tell me if I "
                                   "guessed the right number or so that I could keep guessing your number: ")
            if player_A_reply == "Low":
                while True:
                    random37_low = random.randrange(37, 50, 1)
                    print("Is this your number {}, player A?".format(random37_low))
                    player_A_reply = input("Please type 'Low', 'High', or 'That is the number' to tell me if I "
                                           "guessed the right number or so that I could keep guessing your number: ")
                    if player_A_reply == "That is the number":
                        print("Yay! I guessed the right number:)")
                        break

            if player_A_reply == "High":
                while True:
                    random37_high = random.randrange(25, 37,1 )
                    print("Is this your number {}, player A?".format(random37_high))
                    player_A_reply = input("Please type 'Low', 'High', or 'That is the number' to tell me if I "
                                           "guessed the right number or so that I could keep guessing your number: ")
                    if player_A_reply == "That is the number":
                        print("Yay! I guessed the right number:)")
                        break

            if player_A_reply == "That is the number":
                print("Yay! I guessed the right number:)")
                break
    elif player_A_reply == "High":
        print("Is your number 13?")
        while True:
            player_A_reply = input("Please type 'Low', 'High', or 'That is the number' to tell me if I "
                                   "guessed the right number or so that I could keep guessing your number: ")
            if player_A_reply == "Low":
                while True:
                    random13_low = random.randrange(13,25,1)
                    print("Is this your number {}, player A?".format(random13_low))
                    player_A_reply = input("Please type 'Low', 'High', or 'That is the number' to tell me if I "
                                           "guessed the right number or so that I could keep guessing your number: ")
                    if player_A_reply == "That is the number":
                        print("Yay! I guessed the right number:)")
                        break

            if player_A_reply == "High":
                while True:
                    random13_high = random.randrange(1, 13, 1)
                    print("Is this your number {}, player A?".format(random13_high))
                    player_A_reply = input("Please type 'Low', 'High', or 'That is the number' to tell me if I "
                                           "guessed the right number or so that I could keep guessing your number: ")
                    if player_A_reply == "That is the number":
                        print("Yay! I guessed the right number:)")
                        break

            if player_A_reply == "That is the number":
                print("Yay! I guessed the right number:)")
                break

    elif player_A_reply == "That is the number":
        print("Yay! I guessed the right number:)")

if player_A_reply == "That is the number":
    print("Yay! I guessed the right number:)")


```


-Optional (Player A):
```.py
import random
#generate random number for player A
player_A_number = random.randrange(1,100,1)


#letting player B to guess and return High or Low or Correct number based on the number player B input
while True:
    player_B_guess_number = int(input("Player B, please input 1 integer between 1~100 to see if"
                                      "it is player A's secret number:"))

    if player_B_guess_number > player_A_number:
        print("High")

    if player_B_guess_number < player_A_number:
        print("Low")

    if player_B_guess_number == player_A_number:
        print("That is the number that player A guessed")
        break

````
