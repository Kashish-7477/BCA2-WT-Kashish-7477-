# Basic Programming Concepts

> **Self-Study Prerequisite** | Estimated Time: 3–4 Hours | No Prior Knowledge Required

---

## Learning Objectives

By the end of this self-study module, you should be able to:

- Understand what programming is and why we need it
- Explain variables, data types, and operators
- Write and trace simple loops (`for`, `while`)
- Understand functions as reusable blocks of code
- Work with arrays (lists of items)

---

## 1. What Is Programming?

**Programming** is giving **step-by-step instructions** to a computer to perform a task.

### Real-World Analogy

Programming is like writing a **recipe**:

| Recipe Step | Programming Equivalent |
|------------|----------------------|
| "Take 2 cups of flour" | Store a value: `flour = 2` |
| "If dough is sticky, add more flour" | Condition: `if (sticky) { addFlour() }` |
| "Knead for 10 minutes" | Loop: `repeat 10 times { knead() }` |
| "Serve on a plate" | Output: `print("Done!")` |

A **programming language** is the language we use to write these instructions. We will use **JavaScript** in this course (Unit 5), but the concepts below apply to **all** programming languages.

---

## 2. Variables — Named Storage Boxes

A **variable** is a named container that holds a value. Think of it as a **labelled box**.

### Analogy

```
┌─────────────┐    ┌──────────────┐    ┌───────────────┐
│  name       │    │  age         │    │  city         │
│  "Rahul"    │    │  19          │    │  "Mandsaur"   │
└─────────────┘    └──────────────┘    └───────────────┘
```

### In JavaScript

```javascript
var name = "Rahul";       // A text value (string)
var age = 19;             // A number value
var city = "Mandsaur";    // Another text value
var isStudent = true;     // A true/false value (boolean)
```

### Rules for Variable Names

| Rule | ✅ Correct | ❌ Wrong |
|------|-----------|---------|
| Start with a letter or `_` | `myName`, `_count` | `123abc`, `@name` |
| No spaces | `firstName` | `first name` |
| Case-sensitive | `age` ≠ `Age` ≠ `AGE` | — |
| Use meaningful names | `studentName` | `x`, `a1` |

---

## 3. Data Types — What Kind of Value?

Every value in programming has a **type**. The main types are:

| Data Type | What It Stores | Examples |
|-----------|---------------|---------|
| **String** | Text (in quotes) | `"Hello"`, `"Mandsaur"`, `"25BCA060"` |
| **Number** | Numeric values | `42`, `3.14`, `-10`, `0` |
| **Boolean** | True or False | `true`, `false` |

### Why Types Matter

The computer treats different types differently:

```javascript
// Number addition
var a = 5;
var b = 3;
var sum = a + b;      // Result: 8 (mathematical addition)

// String "addition" (joining/concatenation)
var first = "Rahul";
var last = "Sharma";
var full = first + " " + last;  // Result: "Rahul Sharma" (text joined)
```

**Important:** `"5" + "3"` = `"53"` (text joining), but `5 + 3` = `8` (math).

---

## 4. Operators — Doing Things with Values

### Arithmetic Operators (Math)

| Operator | Meaning | Example | Result |
|----------|---------|---------|--------|
| `+` | Addition | `5 + 3` | `8` |
| `-` | Subtraction | `10 - 4` | `6` |
| `*` | Multiplication | `6 * 7` | `42` |
| `/` | Division | `15 / 3` | `5` |
| `%` | Remainder (Modulo) | `10 % 3` | `1` |

### Comparison Operators (Comparing Values)

| Operator | Meaning | Example | Result |
|----------|---------|---------|--------|
| `==` | Equal to | `5 == 5` | `true` |
| `!=` | Not equal to | `5 != 3` | `true` |
| `>` | Greater than | `10 > 5` | `true` |
| `<` | Less than | `3 < 1` | `false` |
| `>=` | Greater than or equal | `5 >= 5` | `true` |
| `<=` | Less than or equal | `3 <= 4` | `true` |

### Logical Operators (Combining Conditions)

| Operator | Meaning | Example | Result |
|----------|---------|---------|--------|
| `&&` | AND (both must be true) | `true && false` | `false` |
| `\|\|` | OR (at least one true) | `true \|\| false` | `true` |
| `!` | NOT (reverses) | `!true` | `false` |

---

## 5. Conditional Statements — Making Decisions

A **conditional statement** lets your program choose between different actions based on a condition.

### The `if-else` Statement

```javascript
var age = 19;

if (age >= 18) {
    // This runs if age is 18 or more
    alert("You are an adult.");
} else {
    // This runs if age is less than 18
    alert("You are a minor.");
}
```

### The `if-else if-else` Chain

```javascript
var marks = 75;

if (marks >= 90) {
    alert("Grade: A+");
} else if (marks >= 80) {
    alert("Grade: A");
} else if (marks >= 70) {
    alert("Grade: B");
} else if (marks >= 60) {
    alert("Grade: C");
} else {
    alert("Grade: F — Need Improvement");
}
// Output: "Grade: B" (because 75 >= 70)
```

### Real-World Analogy

```
IF it is raining:
    Take an umbrella
ELSE IF it is sunny:
    Wear sunglasses
ELSE:
    Just go normally
```

---

## 6. Loops — Repeating Actions

A **loop** repeats a block of code multiple times. Instead of writing the same line 100 times, you write it once inside a loop.

### The `for` Loop

Use when you know **how many times** to repeat:

```javascript
// Print numbers 1 to 5
for (var i = 1; i <= 5; i++) {
    console.log("Number: " + i);
}
```

**Output:**
```
Number: 1
Number: 2
Number: 3
Number: 4
Number: 5
```

**Breaking down `for (var i = 1; i <= 5; i++)`:**

| Part | Meaning |
|------|---------|
| `var i = 1` | **Start:** Begin counting from 1 |
| `i <= 5` | **Condition:** Keep going as long as i is ≤ 5 |
| `i++` | **Step:** Add 1 to i after each round |

### The `while` Loop

Use when you **don't know** how many times to repeat:

```javascript
var password = "";

while (password != "secret123") {
    password = prompt("Enter the password:");
}

alert("Access granted!");
```

This keeps asking for the password until the user types `"secret123"`.

### Loop Analogy

**`for` loop** = Running laps on a track: "Run 5 laps" (fixed count)

**`while` loop** = Running until you're tired: "Run until you can't anymore" (condition-based)

### Danger: Infinite Loops

If your condition **never becomes false**, the loop runs forever and crashes the browser:

```javascript
// NEVER DO THIS — infinite loop!
while (true) {
    console.log("This never stops!");
}
```

---

## 7. Functions — Reusable Blocks of Code

A **function** is a named block of code that performs a specific task. You can **call** it whenever you need it.

### Why Functions?

Without functions:
```javascript
// Calculate area of rectangle (copy-pasted 3 times)
var area1 = 10 * 5;
var area2 = 8 * 3;
var area3 = 12 * 7;
```

With a function:
```javascript
function calculateArea(length, width) {
    return length * width;
}

var area1 = calculateArea(10, 5);   // 50
var area2 = calculateArea(8, 3);    // 24
var area3 = calculateArea(12, 7);   // 84
```

### Parts of a Function

```javascript
function greetStudent(name) {
    var message = "Welcome, " + name + "!";
    return message;
}

var greeting = greetStudent("Priya");
// greeting = "Welcome, Priya!"
```

| Part | Example | Purpose |
|------|---------|---------|
| **Name** | `greetStudent` | Identifies the function |
| **Parameters** | `(name)` | Input values it receives |
| **Body** | `{ ... }` | The code that runs |
| **Return** | `return message` | The output/result |
| **Call** | `greetStudent("Priya")` | Running the function |

### Real-World Analogy

A function is like a **vending machine**:
- **Input** (parameter): Insert ₹10 coin and press button #3
- **Processing** (body): Machine finds item #3 and drops it
- **Output** (return): You get a packet of chips

You don't need to know **how** the machine works inside — you just use it. That's **abstraction**.

---

## 8. Arrays — Lists of Items

An **array** is a variable that holds **multiple values** in a numbered list.

### Creating an Array

```javascript
var fruits = ["Apple", "Mango", "Banana", "Guava"];
var marks = [85, 92, 78, 90, 65];
```

### Accessing Items (Index starts at 0!)

```
Index:    0        1        2        3
        ┌────────┬────────┬────────┬────────┐
fruits: │ Apple  │ Mango  │ Banana │ Guava  │
        └────────┴────────┴────────┴────────┘
```

```javascript
var first = fruits[0];   // "Apple"
var second = fruits[1];  // "Mango"
var last = fruits[3];    // "Guava"
```

**Common mistake:** The first item is at index `0`, not `1`!

### Useful Array Operations

```javascript
var fruits = ["Apple", "Mango", "Banana"];

// How many items?
fruits.length;           // 3

// Add to end
fruits.push("Guava");   // ["Apple", "Mango", "Banana", "Guava"]

// Remove from end
fruits.pop();            // removes "Guava"

// Loop through all items
for (var i = 0; i < fruits.length; i++) {
    console.log(fruits[i]);
}
// Output: Apple, Mango, Banana
```

### Real-World Analogy

An array is like a **train with numbered coaches**:
- Coach 0: Apple
- Coach 1: Mango
- Coach 2: Banana

You access a specific coach by its **number** (index).

---

## 9. Putting It All Together — A Complete Example

Here's a small program that uses **all** the concepts above:

```javascript
// Variables and data types
var students = ["Anjali", "Bharat", "Chetan", "Deepa", "Esha"];
var marks = [85, 45, 72, 91, 58];

// Function to check pass/fail
function getResult(mark) {
    if (mark >= 50) {
        return "PASS";
    } else {
        return "FAIL";
    }
}

// Loop through all students
for (var i = 0; i < students.length; i++) {
    var result = getResult(marks[i]);
    console.log(students[i] + " scored " + marks[i] + " — " + result);
}
```

**Output:**
```
Anjali scored 85 — PASS
Bharat scored 45 — FAIL
Chetan scored 72 — PASS
Deepa scored 91 — PASS
Esha scored 58 — PASS
```

### Concepts Used

| Line(s) | Concept |
|---------|---------|
| `var students = [...]` | Array + Variables |
| `function getResult(mark)` | Function with parameter |
| `if (mark >= 50)` | Conditional statement |
| `return "PASS"` | Return value from function |
| `for (var i = 0; ...)` | For loop |
| `students[i]` | Accessing array by index |
| `students[i] + " scored "` | String concatenation |

---

## 10. Practice Exercises

Try these on paper (or in your browser console — press `F12` → Console tab):

### Exercise 1: Variables
Create variables to store your name, age, and enrollment number. Print them.

### Exercise 2: Conditional
Write an `if-else` statement that checks if a number is **even** or **odd**.
(Hint: A number is even if `number % 2 == 0`)

### Exercise 3: Loop
Write a `for` loop that prints the multiplication table of 7 (7×1=7, 7×2=14, ... 7×10=70).

### Exercise 4: Function
Write a function `celsiusToFahrenheit(celsius)` that converts Celsius to Fahrenheit.
Formula: `F = (C × 9/5) + 32`

### Exercise 5: Array
Create an array of 5 Indian cities. Use a loop to print each city.

---

## Self-Assessment Questions

1. What is a variable? Why do we give variables meaningful names?
2. What is the difference between a **String** and a **Number**?
3. What will `"10" + "20"` produce? Why?
4. Write a `for` loop that prints numbers from 10 down to 1.
5. What is the difference between a `for` loop and a `while` loop?
6. What is a function? What are its four parts?
7. If `var arr = ["A", "B", "C", "D"]`, what is `arr[2]`?

---

## Quick Summary

| Concept | What It Is | Example |
|---------|-----------|---------|
| Variable | Named storage box | `var age = 19;` |
| String | Text value | `"Hello"` |
| Number | Numeric value | `42`, `3.14` |
| Boolean | True/False | `true`, `false` |
| Operator | Performs operations | `+`, `-`, `==`, `&&` |
| Condition | Decision making | `if (x > 10) { ... }` |
| For Loop | Repeat N times | `for (var i=0; i<5; i++)` |
| While Loop | Repeat until condition false | `while (x < 100)` |
| Function | Reusable code block | `function add(a, b) { return a+b; }` |
| Array | List of values | `["Apple", "Mango", "Banana"]` |

---

*This is a self-study prerequisite for the Web Technology (25BCA060) course at Mandsaur University.*
