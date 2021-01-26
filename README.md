# Hard Parts: Functional JS Foundations

Functional programming - a paradigm for structuring our complex code

## 1. Functional programming::Intro

**Let’s suppose we have a quiz game we’re building**
Every line of code either saves data to memory (e.g. a user’s score) or uses that data (e.g. increase that user’s score)

But with 1000s of lines of code - every line of code can potentially use (and **depend**) on that data!

High risk - every time I want to change any line, I have to consider whether it could affect other lines (and when I miss
something, I get bugs)

What’s the answer?

### The answer has been functions

**Compartmentalise** - Reduce the potential impact of any given line to maybe 10 other lines (inside the function)

**But** even within a 10 line function, ‘reasoning’ through what each line does is hard - & the code may still have
affects outside the function (via global variables)

Functions as we know them may not be enough!

### Imagine if we could structure our code into individual pieces where almost every single line is self-contained

- The only thing any given line depends on are inputs (explicitly stated in that very line)
- The only consequences of the line would be its output (explicitly stated in that very line)
- And each line could get a nice human-readable label for when we use it!

This could transform how we write code, debug it and read about others’ code.

But how could we do it!?

### Functional programming

**Tiny functions**: Save every single line (or few lines) as its own function

**No consequences** except on that line Each function’s only "consequence" is to have its result given to specifically the
next line of code (‘function call’) and not to any other lines

**Recombine/compose** Build up our application by using these small blocks of self-contained code combining them up line-by-line by referring to their human-readable name

## Credits

All credits goes for will sentance course "Hard Parts: Functional JS Foundations" in front end master
