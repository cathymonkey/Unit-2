# AdventofCode 2020 
## Day 2:
Codes:

-Part 1 + Part 2:
```.py

file_input = 'adventcode_2.txt'
counter_1  = 0 #Part 1
counter_2  = 0 #Part 2

with open(file_input, 'r') as file:
    for i in file:
        input           = i.split(': ')
        password        = input[-1]

        validator_txt   = input[0].split(' ')

        occurence_range = validator_txt[0].split('-')

        letter          = validator_txt[-1]


        password_count  = password.count(letter)


        #Part 1
        if password_count >= int(occurence_range[0]) and password_count <= int(occurence_range[1]):
            counter_1 += 1

        #Part 2
        password_pos = [password[int(occurence_range[0])-1], password[int(occurence_range[1])-1]]
        if password_pos.count(letter) == 1:
            counter_2 += 1


    print('Part 1: ', counter_1)
    print('Part 2: ', counter_2)


```
### My solution for Part 1 is 625.

### My solution for Part 2 is 391
