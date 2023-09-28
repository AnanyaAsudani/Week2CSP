---
layout: post
title: 1.4 Correcting errors
description: Practice with identifying and correcting code blocks
type: ccc
author: Safin Singh and Rohan Juneja
permalink: /basics/js-debug
hide: True
---

{% include nav_basics.html %}

[College Board Big Idea 1](https://apclassroom.collegeboard.org/103/home?unit=1)

## Identifying and Correcting Errors (Unit 1.4)

> Become familiar with types of errors and strategies for fixing them

- Review CollegeBoard videos and take notes on blog
- Complete assigned MCQ questions if applicable

# Code Segments

Practice fixing the following code segments!

## Segment 1: Alphabet List

Intended behavior: create a list of characters from the string contained in the variable `alphabet`

### Code:


```python
%%js

var alphabet = "abcdefghijklmnopqrstuvwxyz";
var alphabetList = [];

for (var i = 0; i < 10; i++) {
	alphabetList.push(i);
}

console.log(alphabetList);
```

### What I Changed

I changed...

## Segment 2: Numbered Alphabet

Intended behavior: print the number of a given alphabet letter within the alphabet. For example:
```
"_" is letter number _ in the alphabet
```

Where the underscores (_) are replaced with the letter and the position of that letter within the alphabet (e.g. a=1, b=2, etc.)

### Code:


```python
%%js

// Copy your previous code to built alphabetList here

let letterNumber = 5

for (var i = 0; i < alphabetList; i++) {
	if (i === letterNumber) {
		console.log(letterNumber + " is letter number 1 in the alphabet")
	}
}

// Should output:
// "e" is letter number 5 in the alphabet
```

### What I Changed

I changed...

## Segment 3: Odd Numbers

Intended behavior: print a list of all the odd numbers below 10

### Code:


```python
%%js

let evens = [];
let i = 0;

while (i <= 10) {
  evens.push(i);
  i += 2;
}

console.log(evens);
```

### What I Changed

I changed...

# BELOW NOT EDITED

The intended outcome is printing a number between 1 and 100 once, if it is a multiple of 2 or 5 
- What values are outputted incorrectly. Why?
- Make changes to get the intended outcome.


```python
%%js

var numbers = []
var newNumbers = []
var i = 0

while (i < 100) {
    numbers.push(i)
    i += 1
}
for (var i of numbers) {
    if (numbers[i] % 5 === 0)
        newNumbers.push(numbers[i])
    if (numbers[i] % 2 === 0)
        newNumbers.push(numbers[i])
}
console.log(newNumbers) 


```

# Challenge

This code segment is at a very early stage of implementation.
- What are some ways to (user) error proof this code?
- The code should be able to calculate the cost of the meal of the user

Hint:
- write a “single” test describing an expectation of the program of the program
- test - input burger, expect output of burger price
- run the test, which should fail because the program lacks that feature
- write “just enough” code, the simplest possible, to make the test pass

Then repeat this process until you get program working like you want it to work.


```python
%%js

var menu =  {"burger": 3.99,
         "fries": 1.99,
         "drink": 0.99}
var total = 0

//shows the user the menu and prompts them to select an item
console.log("Menu")
for (var item in menu) {
    console.log(item + "  $" + menu[item].toFixed(2)) //why is toFixed used?
}
//ideally the code should support mutliple items
var item = "burger"

//code should add the price of the menu items selected by the user 
console.log(total)
```

## Hacks
- Fix the errors in the first three segments in this notebook and say what you changed in the code cell under "What I Changed" (Challenge is optional)

# Segment 1


```python
%%js

var alphabet = "abcdefghijklmnopqrstuvwxyz";
var alphabetList = [];

for (var i = 0; i < alphabet.length; i++) {
    alphabetList.push(alphabet[i]);
}

console.log(alphabetList);
```


    <IPython.core.display.Javascript object>


### What I Changed

In the original code, there was a loop set to run only 10 times, which resulted in the creation of a list containing numbers from 0 to 9. To achieve the intended behavior of creating a list of characters from the alphabet string, I made two key changes. First, I modified the loop condition to iterate over the entire length of the alphabet string, ensuring that each character is processed. Second, I updated the code within the loop to push characters from the alphabet string into the alphabetList array instead of numbers. These changes ensure that the code correctly generates a list of characters from the alphabet string, aligning with the desired outcome.

# Segment 2


```python
%%js

%%js

var alphabet = "abcdefghijklmnopqrstuvwxyz";
var alphabetList = [];

for (var i = 0; i < alphabet.length; i++) {
    alphabetList.push(alphabet[i]);
}

console.log(alphabetList);

for (var i = 0; i < alphabet.length; i++) {
    alphabetList.push(alphabet[i]);
}

let letterNumber = 5;

for (var i = 0; i < alphabetList.length; i++) {
    if (alphabetList[i] === alphabet[letterNumber - 1]) {
        console.log('"' + alphabetList[i] + '" is letter number ' + (letterNumber) + ' in the alphabet');
    }
}

// Output should be:
// "e" is letter number 5 in the alphabet
```


    <IPython.core.display.Javascript object>


### What I Changed

I made several changes to the code to achieve the intended behavior of printing the number of a given alphabet letter within the alphabet. First, I initialized the alphabet string and created the alphabetList array to hold the individual letters. Then, I modified the loop condition to ensure it iterates through the alphabetList array. I also adjusted the if condition to compare each element in alphabetList with the corresponding letter in the alphabet string, accounting for the correct letter position. Finally, in the console.log statement, I updated the output format to display the letter and its position within the alphabet, considering that array indices start from 0. These changes ensure that the code correctly outputs messages like "e" is letter number 5 in the alphabet" when letterNumber` is set to 5.

# Segment 3


```python
%%js

let odds = [];
let i = 1; // Start from 1, the first odd number

while (i < 10) {
  odds.push(i);
  i += 2; // Increment by 2 to get the next odd number
}

console.log(odds);

// Output should be: [1, 3, 5, 7, 9]
```

### What I Changed

I made several changes to the code to achieve the intended behavior of printing a list of all odd numbers below 10. First, I renamed the array to odds to clarify its purpose. Then, I initialized the variable i to 1, which represents the first odd number. I adjusted the loop condition to i < 10 to ensure that we collect only odd numbers below 10. Inside the loop, I added the current value of i to the odds array and incremented i by 2 in each iteration to obtain the next odd number. These changes ensure that the code correctly generates and prints a list of odd numbers, including 1, 3, 5, 7, and 9.

# Challenge


```python
%%js

var menu = {
    "burger": 3.99,
    "fries": 1.99,
    "drink": 0.99
};

var total = 0;

// Function to calculate the total cost based on selected items and menu
function calculateTotal(selectedItems, menu) {
    var total = 0;
    for (var item of selectedItems) {
        if (menu.hasOwnProperty(item)) {
            total += menu[item];
        } else {
            console.error("Invalid item selected: " + item);
        }
    }
    return total.toFixed(2);
}

// Test Case: Calculate the price of a burger
var selectedItems = ["burger"];
var expectedTotal = 3.99; // Expected total price for the selected items

// Calculate the actual total based on the selected items
var actualTotal = calculateTotal(selectedItems, menu);

// Check if the actual total matches the expected total
if (actualTotal === expectedTotal) {
    console.log("Test passed: Burger price calculation is correct.");
} else {
    console.error("Test failed: Burger price calculation is incorrect.");
}

```


    <IPython.core.display.Javascript object>


The code above defines a menu object containing items and their respective prices, initializes a total variable to track the cost of selected items, creates a function called calculateTotal to compute the total cost based on user-selected items from the menu, and includes a test case to verify the accuracy of calculating the cost of a single menu item (e.g., a burger). The test case compares the expected total cost with the actual total calculated by the function and logs either a test passed or test failed message. This code forms the foundation for a menu-based system that calculates the total cost of selected items, with room for further expansion and testing.
