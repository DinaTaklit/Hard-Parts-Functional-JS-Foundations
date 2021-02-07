# Hard Parts: Functional JS Foundations

Functional programming - a paradigm for structuring our complex code

## 0. Intro

### 0.1 Functional programming::Intro

**Let’s suppose we have a quiz game we’re building**
Every line of code either saves data to memory (e.g. a user’s score) or uses that data (e.g. increase that user’s score)

But with 1000s of lines of code - every line of code can potentially use (and **depend**) on that data!

High risk - every time I want to change any line, I have to consider whether it could affect other lines (and when I miss
something, I get bugs)

What’s the answer?

#### The answer has been functions

**Compartmentalise** - Reduce the potential impact of any given line to maybe 10 other lines (inside the function)

**But** even within a 10 line function, ‘reasoning’ through what each line does is hard - & the code may still have
affects outside the function (via global variables)

Functions as we know them may not be enough!

#### Imagine if we could structure our code into individual pieces where almost every single line is self-contained

- The only thing any given line depends on are inputs (explicitly stated in that very line)
- The only consequences of the line would be its output (explicitly stated in that very line)
- And each line could get a nice human-readable label for when we use it!

This could transform how we write code, debug it and read about others’ code.

But how could we do it!?

#### Functional programming

**Tiny functions**: Save every single line (or few lines) as its own function

**No consequences** except on that line Each function’s only "consequence" is to have its result given to specifically the
next line of code (‘function call’) and not to any other lines

**Recombine/compose** Build up our application by using these small blocks of self-contained code combining them up line-by-line by referring to their human-readable name

### 0.2 Functional Programming Benefits & Concepts

#### We could produce a beautiful "to do list" of our code

```javascript
pipe(
 getPlayerName,
 getFirstName,
 properCase,
 addUserLabel,
 createUserTemplate
)([{name: 'will sentance', score: 3}]);
```

And render to the webpage

Combining our functions is going to require a ton of interesting techniques to:

- rejoin these ‘lines’ of code (tiny functions) into full-sized tasks:
- make it easy to reuse these functions all over the place
- ensure that the tiny functions truly are self-contained

We’re going to see many of these techniques today

#### (1) Higher order functions, (2) Function composition

- A lot these atoms of code (tiny functions) will be reusable

  - They’re small enough that they’re tasks like incrementing a number, looping through an array
  - We want to write once, use again and again - even for tasks that are not quite identical - keeping our code DRY

#### (3) Pure functions, Immutability of state

We cannot have our lines of code rely on any external data except their explicitly stated inputs

It’s especially important when you’re reusing/ recombining lots of these little single-step functions in lots of totally different scenarios - they better be self contained!

#### (4) Closure, (5) Function Decoration (6) Partial application & Currying

We will need ways to:

- Adjust the functions in case they don’t quite fit together as initially saved
- Give our functions extra features without having to write a new function from scratch.

#### If we can do all that, our code will become

- **More readable** - every line of code has a name that indicates its goal known as "declarative" programming
- **Easier to debug** - Each line of code is an individual unit with clear input and output - no unexpected consequences of using that line ("function")
- **Easier to add features** - most new things we want do do are combinations of something we’ve done elsewhere in our app

#### Our end and beginning

Functions become reusable, versatile, flexible piece of code - a series of independent self-contained readable and predictable steps passing data from one to the next

But it all starts with us being confident with the core principles of JavaScript

## 1.Principles of JavaScript

### What happens when javascript executes (runs) my code?

```javascript
const num = 3;
const multiplyBy2 = (inputNumber) => {
 const result = inputNumber*2;
 return result;
}
const name = "Will"
```

Code is saved (defined) in functions - to be run later
As soon as we start running our code, we create a **global execution context**

- Thread of execution (parsing and executing the code line after line)
- Live memory of variables with data (known as a Global Variable Environment)

### Running/calling/invoking a function

This is not the same as defining a function

```javascript
const num = 3;
const multiplyBy2 = (inputNumber) => {
 const result = inputNumber*2;
 return result;
}
const output = multiplyBy2(num);
const newOutput = multiplyBy2(10);
```

When we execute a function it creates a **new execution context** comprising:

1. The thread of execution (we go through the code in the function line by line)
2. A local memory ("Variable environment") where anything defined in the function is stored

### We keep track of the functions being called in JavaScript with a Call stack

- Tracks which execution context we are in - that is, what function is currently being run and where to return to
after an execution context is popped off the stack

- One global execution context, multiple function
contexts

## Credits

All credits goes for will sentance course "Hard Parts: Functional JS Foundations" in front end master
