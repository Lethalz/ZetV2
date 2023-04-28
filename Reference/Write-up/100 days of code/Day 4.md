
What i learned : 

Module - can import modules into main.py
Randomisation
Lists
Split String method
Nested lists
# Projects

Heads and Tails 
```Python
import random

rand_nums = random.randint(0, 1)
if rand_nums == 1:
  print("Tails")
else: print("Heads")
```

Split the bill A

```Python
import random

#Asks the User for everyone's names
names_string = input("Give me everybody's names, sepearted by a comma.")
#Converts those names into a list using the .split function
names = names_string.split(", ")
# Picks a random number from 0 to 2
rand_nums = random.randint(0,2)
#Uses that randomly generated number to pick a name out of the created list
if rand_nums == 1:
  print(names[0],"has to pay the bill!")
  if rand_nums == 2:
    print(names[1],"has to pay the bill!")
else: print(names[2],"has to pay the bill!")
```

Split the bill B

```Python 
import random
#Asks the User for everyone's names
names_string = input("Give me everybody's names, seperated by a comma.\n")
#Converts those names into a list using the .split function
names = names_string.split(", ")
#Uses .choice to pick a random choice from the 'names' list the user provided
random_name = random.choice(names)
#Prints name
print(random_name)
```


Treasure map
```Python

row1 = ["😂","😂","😂"]
row2 = ["😂","😂","😂"]
row3 = ["😂","😂","😂"]
map = [row1, row2, row3]
print(f"{row1}\n{row2}\n{row3}")
position = input("Where do you want to put the treasure?")

# Since both coordinates are single digits, there is no need to split the input string.
# However, if the user were to input a string with more than two characters, the code would not work correctly. In that case, you would need to split the input string into separate substrings for each coordinate using the `split()` method or some other method of string manipulation.
horizontal = int(position[0])
vertical = int(position[1])

# This line selects the row e.g map[1] and puts it into a variable for changing.
selected_row = map[vertical - 1]
# This row takes that variable picks a position out the row and replaces it with 'X'
selected_row[horizontal - 1] = "X"


## map[vertical - 1]horizontal - 1] = "X"


print(f"{row1}\n{row2}\n{row3}")
```




Rock, Paper, Scissors

```Python
import random

rock = '''
    _______
---'   ____)
      (_____)
      (_____)
      (____)
---.__(___)
'''

paper = '''
    _______
---'   ____)____
          ______)
          _______)
         _______)
---.__________)
'''

scissors = '''
    _______
---'   ____)____
          ______)
       __________)
      (____)
---.__(___)
'''

game_images = [rock, paper, scissors]

user_choice = int(input("What do you choose? Type 0 for Rock, 1 for Paper or 2 for Scissors.\n"))
print(game_images[user_choice])

computer_choice = random.randint(0, 2)
print("Computer chose:")
print(game_images[computer_choice])

if user_choice >= 3 or user_choice < 0: 
  print("You typed an invalid number, you lose!") 
elif user_choice == 0 and computer_choice == 2:
  print("You win!")
elif computer_choice == 0 and user_choice == 2:
  print("You lose")
elif computer_choice > user_choice:
  print("You lose")
elif user_choice > computer_choice:
  print("You win!")
elif computer_choice == user_choice:
  print("It's a draw")
```