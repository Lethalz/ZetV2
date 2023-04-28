


```Python
print("Welcome to the tip calculator.\n")
bill = input ("What is the bills total?\n")
new_bill = float(bill) 
people = input ("How many people to split the bill?\n")
new_p = float(people)
tip = input("What percentage tip would youy like to give? 10, 12, or 15?\n")
new_tip = float(tip)
newnewtip = (new_tip/100) * new_bill
print("Each person should pay:", (new_bill + newnewtip) / new_p)



#If the bill was $150.00, split between 5 people, with 12% tip. 
#Each person should pay (150.00 / 5) * 1.12 = 33.6
#Round the result to 2 decimal places.
print("Welcome to the tip calculator!")
bill = float(input("What was the total bill? $"))
tip = int(input("How much tip would you like to give? 10, 12, or 15? "))
people = int(input("How many people to split the bill?"))

tip_as_percent = tip / 100
total_tip_amount = bill * tip_as_percent
total_bill = bill + total_tip_amount
bill_per_person = total_bill / people
final_amount = round(bill_per_person, 2)


# FAQ: How to round to 2 decimal places?

# Find the answer in the Q&A here: https://www.udemy.com/course/100-days-of-code/learn/lecture/17965132#questions/13315048


print(f"Each person should pay: ${final_amount}"
```




What we learned on day 2: 
-   On the second day of the course, we learned how to use Python to calculate a tip and split a bill between multiple people.
-   We started by using the `print()` function to display a welcome message and prompt the user for input.
-   We used the `float()` function to convert a string input into a floating-point number, which allowed us to perform mathematical operations on it.
-   We also used the `int()` function to convert a string input into an integer, which was used to calculate the tip as a percentage.
-   Next, we used arithmetic operators, such as multiplication and division, to calculate the total tip amount, the total bill (including tip), and the bill per person.
-   Finally, we used the `round()` function to round the bill per person to two decimal places and displayed the result using the `print()` function with an `f-string` notation that included variables and expressions.

