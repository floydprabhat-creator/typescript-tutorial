# Day 01 — Assignment: TypeScript Basics & Variables

> Based on: [`src/notes/day-01.md`](../notes/day-01.md)
> Solutions: [`src/solutions/day-01/`](../solutions/day-01/)

**How to run a solution**

```bash
npm run build                                   # compile everything in src/ → dist/
node dist/solutions/day-01/question1.js         # run one solution
```

---

## Section A — Setup & Transcompilation

### Question 1 — Hello TypeScript (Node.js)
Create a variable `username` of type `string` and print `Hello! <username>` to the console.
Compile it with `tsc` and run the generated `.js` file with Node.

### Question 2 — Browser vs Node.js
Write a program that prints a greeting using `document.write()` when it runs in a browser,
and falls back to `console.log()` when it runs in Node.js (where `document` does not exist).

In a comment, answer:
1. What error do you get if you call `document.write()` in Node.js, and why?
2. Which kind of code should be linked to an HTML page, and which kind can be run directly with Node?

---

## Section B — Variable Phases

### Question 3 — Declaration, Assignment, Initialization
Write a program that clearly demonstrates all three phases of variable configuration.
Label each line with a comment saying which phase it is, then print the final values.

---

## Section C — `var`, `let`, `const`

### Question 4 — `var` is function-scoped
Write a function `showMarks()` that:
- declares `var total` at the top of the function,
- declares `var grade` **inside** an `if` block,
- prints both `total` and `grade` **outside** the `if` block.

Explain in a comment why this works.

### Question 5 — `let` is block-scoped
Rewrite Question 4 using `let` instead of `var`.
1. Show (in a comment) the compiler error you get and why.
2. Then fix the program so it compiles and prints both values.

### Question 6 — `const` rules
For each line below, state whether it is **valid** or **invalid** and give the reason.
Then write a small working program that uses `const` correctly.

```typescript
const PI;
const RATE = 0.5;
RATE = 0.7;
const APP_NAME: string = "TS Tutorial";
```

### Question 7 — Shadowing
1. Show that `var` allows a variable to be re-declared in the same scope.
2. Show (in a comment) what happens when you try the same with `let`.

### Question 8 — Hoisting
1. Write a function that uses a `var` variable **before** it is declared, and prints it.
2. Show (in a comment) what happens if you do the same with `let`.

---

## Section D — Think & Apply

### Question 9 — Predict the output
Without running it, predict the output of the following code. Then run it to verify.

```typescript
function test() {
  var a = 1;
  let b = 2;
  if (true) {
    var a = 10;
    let b = 20;
    console.log("inside:", a, b);
  }
  console.log("outside:", a, b);
}
test();
```

### Question 10 — Choose the right keyword
For each scenario, choose `var`, `let`, or `const` and justify your choice in a comment.
Then write code for each one.

1. The number of days in a week.
2. A counter that increases inside a `for` loop.
3. A user's current score that changes during a game.
4. The base URL of an API.

---

*End of Day 01 Assignment*
