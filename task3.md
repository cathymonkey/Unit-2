## Task 3.md 

### Snakify coding problems:

#### Lesson 6: While loop

##### Problem 1: List of squares
Detail: For a given integer N, print all the squares of integer numbers where the square is less than or equal to N, in ascending order.
My codes:

```.py

first_integer = 0
n = int(input("Input an integer"))


while first_integer <= n:
    print(first_integer ** 2)
    first_integer +=1



```

##### Problem 4: Morning jog
Detail: As a future athlete you just started your practice for an upcoming event. Given that on the first day you run x miles, and by the event you must be able to run y miles.
Calculate the number of days required for you to finally reach the required distance for the event, if you increases your distance each day by 10% from the previous day.

Print one integer representing the number of days to reach the required distance.

My codes:
```.py


first_day_miles = int(input("Input the miles you will run in the first day of the event:"))

goal_miles = int(input("Input the miles you want to have run after the event:"))

day_to_run = 1

while True:

    if first_day_miles == goal_miles:
        print("You need to run 1 day to reach your goal.")
        break

    elif first_day_miles <= goal_miles:
        first_day_miles *= 110
        first_day_miles /= 100
        # print(day_to_run)
        # print(first_day_miles)
        day_to_run += 1


    elif first_day_miles >= goal_miles:
        print("You need to run {} days to reach your goal.".format(day_to_run))
        break

```
