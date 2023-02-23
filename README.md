## Creating a Rock, Paper, Scissors game in Python

As part of a DevOps bootcamp I'm currently in, I dove into some Python fundamentals to familiarize myself with it. For this project, I followed along with a YouTube tutorial from freeCodeCamp.org by Beau Carnes.

[freeCodeCamp YouTube](https://youtu.be/eWRfhZUzrAc)

[My Notion Projects](https://shorturl.at/oyIS6)

### We login and get started with Python.
We learn about variables in Python. Since we're creating a rock, paper, scissors game, we start creating variables for each.

```python
player_choice = "rock"
computer_choice = "paper"
```

In learning about functions, we learn that indentation is key. We define a function, using these variables. Notice the indentation on both variables.

```python
def get_choices():
 player_choice = "rock"
 computer_choice = "paper"
 ```
We next add what variable will be returned when this function is called.

```python
def get_choices():
 player_choice = "rock"
 computer_choice = "paper"
 return player_choice
```

Beau then asks if we can adjust the return line to return the variable for "rock" instead.

```python
def get_choices():
 player_choice = "rock"
 computer_choice = "paper"
 return computer_choice
 ```
 
We now start learning how to call functions. We create a new variable for the function, then call the function.

```python
def get_choices():
 player_choice = "rock"
 computer_choice = "paper"

 return computer_choice

choices = get_choices()
print(choices)
```

When the following code is ran, it displays "paper" without quotations in the console. Next, we covered Dictionaries. Dictionaries in Python are used to store data in key:value pairs. They're distinctive by their curly brackets. We edit the initial code to use dictionaries in Python.

```python
def get_choices():
  player_choice = "rock")
  computer_choice = "paper"
  choices = {"player": player_choice, "computer":computer_choice}
  return choices

choices = get_choices()
print(choices)
```

We then alter the variable for player_choice to use the input function.

```python
def get_choices():
  player_choice = input("Enter a choice (rock, paper, scissors): ")
  computer_choice = "paper"
  choices = {"player": player_choice, "computer":computer_choice}
  return choices

choices = get_choices()
print(choices)
```

When this code is ran, it displays our input function in the console. We're now introduced to libraries. If you import a library, you get access to more features without having to write additional code. For our game we're creating, we need to use the random library.

```python
import random

def get_choices():
  player_choice = input("Enter a choice (rock, paper, scissors): ")
  computer_choice = "paper"
  choices = {"player": player_choice, "computer":computer_choice}
  return choices

choices = get_choices()
print(choices)
```

We then learn about lists. Lists allow us to store multiple items in a single variable. Lists use brackets, with each item separated by a comma. We use a list to create the options variable below. Then, with the random library we imported earlier, we use it to redefine the computer_choice variable.

```python
import random

def get_choices():
  player_choice = input("Enter a choice (rock, paper, scissors): ")
 options = ["rock", "paper", "scissors"]
  computer_choice = random.choice(options)
  choices = {"player": player_choice, "computer":computer_choice}
  return choices

choices = get_choices()
print(choices)
```

We begin learning about function arguments. Functions can receive data when they're called. This data is called arguments. We specify that data here, passing (player, computer) as the data, then remove the choices return from before.

```python
import random

def get_choices():
  player_choice = input("Enter a choice (rock, paper, scissors): ")
 options = ["rock", "paper", "scissors"]
  computer_choice = random.choice(options)
  choices = {"player": player_choice, "computer":computer_choice}
  return choices

def check_win(player, computer):
 return [player, computer]
 ```
 
Next we learn about if statements. If statements will allow a program to do different things depending on certain conditions. We use an if statement to update the return statement in the case of a tie.

```python
def check_win(player, computer):
 if player == computer:
 return "It's a tie!"
 ```
 
With this, if both the player and computer select the same option, it will display the string, "It's a tie!" To allow the user/player to make sure this is true, we can add code to display both the player and the computer's selections using concatenation.

```python
def check_win(player, computer):
 print("You chose: " + player + "Computer chose: " + computer)
 if player == computer:
 return "It's a tie!"
 ```
 
Now we learn how to simplify this process with f-strings.

```python
def check_win(player, computer):
 print(f"You chose: {player}. Computer chose: {computer}.")
 if player == computer:
 return "It's a tie!"
 ```
 
To test this, we add strings for the variables player and computer and run the code.

```python
def check_win(player, computer):
 print(f"You chose: {player}. Computer chose: {computer}.")
 if player == computer:
 return "It's a tie!"

check_win("rock","paper")
```

Currently our game only checks if there's a tie. We learn about else and elif statements now to check other possible outcomes.

```python
def check_win(player, computer):
 print(f"You chose: {player}. Computer chose: {computer}.")
 if player == computer:
  return "It's a tie!"
 elif player == "rock" and computer == "scissors":
  return "Rock smashes scissors? You win!"
 elif player == "rock" and computer == "paper":
  return "Paper covers rock! You lose."

check_win("rock","paper")
```

The code added above checks if there's a tie, else if player is equal to rock and computer is equal to paper, it will return the string "Rock smashes scissors? You win!" If that statement is not true, player is equal to rock and and computer is equal to paper, it returns the string "Paper covers rock! You lose."

This is good, but we need to cover more scenarios. We can do so by refactoring the code in the next task. We learn about refactoring the code to perform the same functionality, just make it more understandable, using a nested if statement.

```python
def check_win(player, computer):
 print(f"You chose: {player}. Computer chose: {computer}.")
 if player == computer:
  return "It's a tie!"
 elif player == "rock":
    if computer == "scissors":
      return "Rock smashes scissors! You win!"
    else:
      return "Paper covers rock. You lose."
  elif player == "paper":
    if computer == "rock":
      return "Paper covers rock! You win!"
    else:
      return "Paper shredded by scissors. You lose."    
  elif player == "scissors":
    if computer == "paper":
      return "Scissors shreds paper! You win!"
  else:
    return "Scissors smashed by rock. You lose."

check_win("rock","paper")
```

We no longer need to assign strings to check_win, but instead assign a new variable for the get_choices function named choices.

```python
def check_win(player, computer):
 print(f"You chose: {player}. Computer chose: {computer}.")
 if player == computer:
  return "It's a tie!"
 elif player == "rock":
    if computer == "scissors":
      return "Rock smashes scissors! You win!"
    else:
      return "Paper covers rock. You lose."
  elif player == "paper":
    if computer == "rock":
      return "Paper covers rock! You win!"
    else:
      return "Paper shredded by scissors. You lose."    
  elif player == "scissors":
    if computer == "paper":
      return "Scissors shreds paper! You win!"
  else:
    return "Scissors smashed by rock. You lose."

choices = get_choices()
```

We next learn how to access dictionary values, which allows us to add another variable that calls the check_win function that passes in the value of the player and computer keys of the choices dictionary. At last, all we have to do is print the result.

Full code with the print function added:

```python
import random

def get_choices():
  player_choice = input("Enter a choice (rock, paper, scissors): ")
  options = ["rock", "paper","scissors"]
  computer_choice = random.choice(options)
  choices = {"player": player_choice, "computer":computer_choice}
  return choices

def check_win(player, computer):
  print(f"You chose: {player}. Computer chose: {computer}.")
  if player == computer:
   return "It's a tie!" 
  elif player == "rock":
    if computer == "scissors":
      return "Rock smashes scissors! You win!"
    else:
      return "Paper covers rock. You lose."
  elif player == "paper":
    if computer == "rock":
      return "Paper covers rock! You win!"
    else:
      return "Paper shredded by scissors. You lose."    
  elif player == "scissors":
    if computer == "paper":
      return "Scissors shreds paper! You win!"
  else:
    return "Scissors smashed by rock. You lose."
    
choices = get_choices()
result = check_win(choices["player"], choices["computer"])
print(result)
```

Now, when we run the code to test that game, it works! This completes the lab.

Overall, I was very impressed with just how straight forward Python is. I have a bit of experience in C# and have been exposed to other languages as well, but Python is the least picky I've ever come across in terms of requiring mark-up to the language syntax.
