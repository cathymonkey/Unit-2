# AdventofCode 2020 
## Day 1:
Codes:

-Part 1 + Part 2:
```.py

with open("adventcode_2.txt", "r") as f:
    data = [line.strip().split(": ") for line in f.readlines()]
    for i in range(len(data)):
        data[i][0] = data[i][0].split(" ")
        data[i][0][0] = data[i][0][0].split("-")

def count_character(char,string):
    count = 0
    for i in string:
        if i == char:
            count+=1
    return count

def validate(passwords):
    valid = []
    for i in passwords:
        if count_character(i[0][1],i[1]) in range(int(i[0][0][0]),int(i[0][0][1])+1):
            valid.append(i[1])
    return len(valid)

print(validate(data))


```
### My solution for Part 1 is 625.

### My solution for Part 2 is 391
