# JS Loops

## Condition-controlled loops
Iterate for a variable number of times, depending on a **boolean** condition

[while loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/while)

Example
```js
var counter = 0;
while (counter < 3) {
    console.log("this is going to log 3 times");
    counter ++;
};
// this is going to log 3 times
// this is going to log 3 times
// this is going to log 3 times
```


## Count-controlled Loops
Iterate for a specific **number** of times

[for loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for)

Example
```js
for (var i = 0; i < 3; i++) {
    console.log("the count is " + 3);
    // i is a variable, think iteration / index
}
// the count is 1
// the count is 2
// the count is 3
```


## For loop with array
We'll be doing a LOT of this

Pretty soon you'll be dreaming about for loops

```js
var myArray = [1, 2, 3]

for (var i = 0; i < myArray.length; i++) {
    console.log(myArray[i]);
    // i is a variable, think iteration / index
}
// 1
// 2
// 3
```


### MEMORIZE THE FOR LOOP SYNTAX
declaration | initial value | condition | final expression operator | execute code
--- | --- | --- | --- | ---
`for` | `var i = 0` | `i < myArray.length` | `i ++` | `console.log(myArray[i])`
declare for loop | set the initial value | write a condition that will stop the loop | run this operator after the code is executed | execute this code every loop<br/>log to console each item in the array
this is a for loop | initial value is 0 | run the loop for as many times as there are items in the array | add 1 each time the code is executed | log the item in the index to the console



## Math and Loop Exercises
[Math.random()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random)

#### 1
Build a program that asks the user to guess a secret number
- randomly generate a number between 1 - 10. store it in a variable.
- ask the user to guess a number 1-10.
- use conditional statements to determine if the user guessed correctly.
- if user guesses correctly, tell them they win.
- if user guesses less than or greater than the number, tell them they're over or under.

#### 2
Rewrite exercise number 1 using a while loop
- let the user guess as many times as needed

#### 3
Now rewrite exercise 1 using a for loop. This time, the user only gets 3 guesses.
- if the user runs out of guesses, tell them they lose.

#### 4
Build a program that prompts the user to enter a number. Find all numbers between 1 and 1000 that are evenly divisible by that number.

#### Bonus: Rock, Paper, Scissors
Build a program that plays rock, paper, scissors with the user
- use Math.random() to select a random option for the computer.
- ask the user to choose "r", "p", or "s"
- using conditional statements, determine the winner and console.log() the result
- rock beats scissors, scissors beats paper, paper beats rock


# 1
## Build a program that asks the user to guess a secret number
- randomly generate a number between 1 - 10. store it in a variable.
- ask the user to guess a number 1-10.
- use conditional statements to determine if the user guessed correctly.
- if user guesses correctly, tell them they win.
- if user guesses less than or greater than the number, tell them they're over or under.

```js
var secretNumber = Math.floor(Math.random() * 10) + 1;

var guess = parseInt(prompt("Guess a number between 1-10"))

if (guess === secretNumber) {
	console.log("You win!");
} else if (guess > secretNumber) {
	console.log('You guessed over!');
} else if (guess < secretNumber) {
	console.log('You guessed under!');
} else {
	console.log('Hmm...not sure what to do with that input');
}
```

### Little safer version
```js
var secretNumber = Math.floor(Math.random() * 10) + 1;

var guess = parseInt(prompt("Guess a number between 1-10"))

if (guess <= 10 && guess >= 1) {
	if (guess > secretNumber) {
		console.log('You guessed over!');
	} else if (guess < secretNumber) {
		console.log('You guessed under!');
	} else {
		console.log('You win!');
	}
} else {
	console.log('Hmm...not sure what to do with that input');
}

```

# 2
## Rewrite exercise number 1 using a while loop

```js
var secretNumber = Math.floor(Math.random() * 10) + 1;

var guess = parseInt(prompt("Guess a number between 1-10"))

var gameOver = false;

while (gameOver === false) { // (!gameOver) works too
	if (guess <= 10 && guess >= 1) {
		if (guess > secretNumber) {
			guess = parseInt(prompt("You guessed " + guess + ". That's too high. Try again!"));
		} else if (guess < secretNumber) {
			guess = parseInt(prompt("You guessed " + guess + ". That's too low. Try again!"));
		} else {
			console.log("You guessed " + guess + ". You win!");
			gameOver = true;
		}
	} else {
		guess = parseInt(prompt("Hm.. not sure what to do with that input. Try again!"))
	}
};
```

# 3
## Rewrite exercise 1 using a for loop. This time, the user only gets 3 guesses.

```js
var secretNumber = Math.floor(Math.random() * 10) + 1;
var userGuess = parseInt(prompt("Guess a number between 1-10"));

if (userGuess >= 1 && userGuess <= 10) {
	forLoop()
}

function forLoop() {
	for (var i = 0; i < 3; i++) {
		if (i === 2) {
			if (userGuess === secretNumber) {
				console.log("You won!");
			} else {
				console.log("You lose!");
			}
		} else {
			if (userGuess === secretNumber) {
				return console.log("You won!")
			} else if (userGuess < secretNumber) {
				userGuess = parseInt(prompt("Nope! Try higher."))
			} else if (userGuess > secretNumber) {
				userGuess = parseInt(prompt("Nope! Try lower."))
			} else {
				userGuess = parseInt(prompt("Hm..not sure what to do with that input. Try again!"))
			}
		}
	};
}
```


# 4
## Build a program that prompts the user to enter a number. Find all numbers between 1 and 1000 that are evenly divisible by that number.

```js
var userNumber = parseInt(prompt("Enter a number between 1-1000"));

for (var i = 1; i <= 1000; i++) {
	if (i % userNumber === 0) {
		console.log(i);
	}
}
```

### Safer version
```js
// declare global variables
var userNumber;
var arrayOfNums = [];

// start the program by invoking a function
askUserForNumber();

// prompts the user, sets the user's number
// invoke another function to check the number
function askUserForNumber() {
	userNumber = parseInt(prompt("Enter a number between 1-1000"));
	checkForNumber(userNumber);
};

// make sure the number is between 1 - 1000
// if so, invoke the next function
// if not, invoke the previous function again
function checkForNumber(num) {
	if (num <= 1000 && num >= 1) {
		createArray(num);
	} else {
		alert("Invalid entry");
		askUserForNumber();
	};
};

// display the results as an array
function createArray(n) {
	console.log("You entered " + userNumber + ". Theses are all the numbers between 1-1000 that are divisible by " + userNumber + ".");

	for (var i = 1; i <= 1000; i++) {
		if (i % n === 0) {
			arrayOfNums.push(i);
		};
	};

	console.log(arrayOfNums);
};
```
