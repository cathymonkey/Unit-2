# AdventofCode 2020 
## Day 1:
Codes:

-Part 1:
```.py

database = open("adventcode_1.txt", "r").read().splitlines()
int_db =[]
for n in range(len(database)):
    int_db.append(int(database[n]))
print(int_db)

for i in range(len(int_db)):
    for y in range(len(int_db)):
        if i != y and int_db[i] + int_db[y] == 2020:
            print(int_db[i],int_db[y])
            print(int_db[i] * int_db[y])

```
### Solution: correct pair of numbers are 661 and 1359. The multiplication of this two numbers is **898299**

-Part 2:
```.py

database = open("adventcode_1.txt", "r").read().splitlines()
int_db =[]
for n in range(len(database)):
    int_db.append(int(database[n]))
print(int_db)

for i in range(len(int_db)):
    for y in range(len(int_db)):
        for z in range(len(int_db)):
            if i != y and y != z and int_db[i] + int_db[y] + int_db[z] == 2020:
                print(int_db[i],int_db[y], int_db[z])
                print(int_db[i] * int_db[y] * int_db[z])

```
### Solution: correct group of numbers are 297, 1369, and 354.The multiplication of these 3 numbers is 143933922
