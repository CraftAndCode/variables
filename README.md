# Variables

```package
core
radio
microphone
```

```template
basic.forever(function () {
})
```

```blocks
basic.forever(function () {
})
```

## Step 0 @showDialog
Hello! Today we're going to teach the Micro:bit to store and update data using variables.

## Step 1 @showDialog
### What is a variable?

Today almost all electronic devices have an amount of memory that can be used to store and access data. In some ways, computer memory is like a warehouse filled with cardboard boxes, both empty and full. If we want to store some information, we put it into a box. Then we label the box so we can find and access that information later.
  
A variable is a container inside the device's memory that is labeled with a specific name. Variables can store sensor readings or track parameters that vary over time, such as a player's health in a computer game.

When a variable is created, it is given a name that can later be used to set, access, or change the contents of that variable.
## Step 2
### Creating a variable
As you can see, a new ``||variables.variables||`` category has appeared in the toolbox, but there are no blocks inside it yet.

Let's click the `|Make a Variable|` button and input a name for your variable! Do you see the new blocks now?

## Step 3 @showDialog
### Get, set, change
Now that we have the new blocks, let's learn what they do and how we can use them!

#### a `set` block
When a variable is created, its value is set to 0 by default. A ``||variables.set||`` block is used to replace this value with something else. 
```block
let player_health = 100
```

#### a `get` block
A ``||variables.get||`` block is a round block that bears the name of your variable. This block is used to get the memorized value and do something with it, for example, to show it on screen.
```block
basic.showNumber(player_health)
```

#### a `change` block
A ``||variables.change||`` block is much the same as a ``||variables.set||`` block but, instead of replacing the value completely, it adds to the values. If, for example, a character in a computer game is healed, the value of its health goes up.
```block
player_health += 10
```
## Step 3.5 @showHint
### Step counter
Let's test these blocks in action! This example is a step counter that can be attached to you ankle. When you take a step, a `shake` gesture occurs, and a ``||variables.steps||`` variable is updated. Then the new value is shown on screen.
```hint
You'll need to create a new variable called `steps`.
```

```blocks
let steps = 0
input.onGesture(Gesture.Shake, function () {
    steps += 1
    basic.showNumber(steps)
})
```

## Step 4 @showHint
### Guess the number!
This example is more complex and uses two variables.
- The ``||variables.secret number||`` variable stores a random number between 1 and 9
- The ``||variables.your guess||`` variable is used to store your guess and can be changed with the `|A|` button
- A ``||logic.if-else||`` condition checks if these two values are equal when the `|B|` button is pressed 
```blocks
let my_guess = 0
let secret_number = 0
secret_number = randint(1, 9)
my_guess = 0
```
```blocks
input.onButtonPressed(Button.A, function () {
    my_guess += 1
    basic.showNumber(my_guess)
})
input.onButtonPressed(Button.B, function () {
    if (secret_number == my_guess) {
        basic.showIcon(IconNames.Yes)
    } else {
        basic.showIcon(IconNames.No)
        my_guess = 0
    }
})

```

## Step 5 @showHint
### Guess the number v.2
Let's improve our last program so it gives us a hint if our number is smaller or larger than the secret one. Change the ``||input.on B button pressed||`` code following the example. Leave the other code as-is.
  
Now you can guess the number in no more than 3 tries. Can you figure it out?
```blocks
input.onButtonPressed(Button.B, function () {
    if (secret_number < my_guess) {
        basic.showString("<")
        my_guess = 0
    } else if (secret_number > my_guess) {
        basic.showString(">")
        my_guess = 0
    } else {
        basic.showIcon(IconNames.Yes)
    }
})
```
## Step 7 @showHint
### Now it's your turn!
Let's improve our program even more! When a guess is correct, make your program think of another secret number and start again.
The next step of the tutorial includes the answer in case you can't figure it out on your own.
```hint
You'll need to add this code to a specific place in your program.
```
```block
secret_number = randint(1, 9)
```

## Step 8 @showDialog
### Answers: Now it's your turn!

```diffblocks
input.onButtonPressed(Button.B, function () {
    if (secret_number < my_guess) {
        basic.showString("<")
        my_guess = 0
    } else if (secret_number > my_guess) {
        basic.showString(">")
        my_guess = 0
    } else {
        basic.showIcon(IconNames.Yes)
        
    }
})
----------
input.onButtonPressed(Button.B, function () {
    if (secret_number < my_guess) {
        basic.showString("<")
        my_guess = 0
    } else if (secret_number > my_guess) {
        basic.showString(">")
        my_guess = 0
    } else {
        basic.showIcon(IconNames.Yes)
        secret_number = randint(1, 9)
    }
})
```

## Step 7 @showHint
### Challenge: Graphical die
This was to have been a program for a graphical die that shows a number of dots when shaken. Alas, our programmers didn't finish it. Can you?
```blocks
let number = 0
input.onGesture(Gesture.Shake, function () {
    number = randint(1, 6)
    if (number == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . # . .
            . . . . .
            . . . . .
            `)
    } else if (number == 2) {
        basic.showLeds(`
            # . . . .
            . . . . .
            . . . . .
            . . . . .
            . . . . #
            `)
    } else if (number == 3) {
        basic.showLeds(`
            . . . . #
            . . . . .
            . . # . .
            . . . . .
            # . . . .
            `)
    } else if (number == 4) {
        
    } else {
        
    }
})
```
## @showHint

### Answers: Graphical die
```blocks
let number = 0
input.onGesture(Gesture.Shake, function () {
    number = randint(1, 6)
    if (number == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . # . .
            . . . . .
            . . . . .
            `)
    } else if (number == 2) {
        basic.showLeds(`
            # . . . .
            . . . . .
            . . . . .
            . . . . .
            . . . . #
            `)
    } else if (number == 3) {
        basic.showLeds(`
            . . . . #
            . . . . .
            . . # . .
            . . . . .
            # . . . .
            `)
    } else if (number == 4) {
        basic.showLeds(`
            # . . . #
            . . . . .
            . . . . .
            . . . . .
            # . . . #
            `)
    } else if (number == 5) {
        basic.showLeds(`
            # . . . #
            . . . . .
            . . # . .
            . . . . .
            # . . . #
            `)
    } else {
        basic.showLeds(`
            # . # . #
            . . . . .
            . . . . .
            . . . . .
            # . # . #
            `)
    }
})
```
## Step 9
We've learned something new today! Now you know what variables are and how to use them.
