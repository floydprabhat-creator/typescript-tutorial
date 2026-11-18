# Day 01 - TypeScript Basics

---

## 1. Project File Structure

| File / Folder | Description |
|---------------|-------------|
| `package.json` | Comprises of project metadata (name, version, author, dependencies, etc.) |
| `tsconfig.json` | Comprises of TypeScript configuration settings |
| `public/` | Comprises of **static** resources — images, HTML, text files, etc. |
| `src/` | Comprises of **dynamic** resources — `.js`, `.ts`, `.css`, `.scss`, etc. |
| `index.html` | The **startup/entry page** for the project |

---

## 2. TypeScript Language Topics Overview

1. Variables
2. Data Types
3. Operators
4. Statements
5. Functions

---

## 3. TypeScript File Basics

> Every TypeScript file has the extension **`.ts`**

### Transcompilation

TypeScript cannot run directly in a browser or Node.js — it must be **transcompiled** into JavaScript first.

```bash
tsc index.ts
```

This generates a corresponding **`index.js`** file. The transcompiler automatically calls the core compiler internally.

---

### When to Use Browser vs Node.js

| Code Type | How to Run |
|-----------|------------|
| Code with DOM / `document` methods | Link `index.js` to an HTML page in browser |
| Code with only `console` methods (no DOM) | Run directly using Node.js |

**Linking JS to HTML:**
```html
<script src="src/index.js"></script>
```

**Running with Node:**
```bash
node index.js
```

> ⚠️ If your code uses `document.write()` and you run it with `node index.js`, it will throw:
> **`ReferenceError: document is not defined`** — because Node.js has no DOM.

---

### Example 1 — Output in Browser

**`src/index.ts`**
```typescript
var username: string = "John";
document.write("Hello! " + username);
```

**Steps:**
1. Go to the `src` folder and create `index.ts`
2. Right-click on `index.ts` → **Open in Integrated Terminal**
3. Transcompile:
   ```bash
   tsc index.ts
   ```
   This generates `index.js` in the same folder.
4. Link in `index.html`:
   ```html
   <head>
     <script src="src/index.js"></script>
   </head>
   ```
5. Open `index.html` with Live Server to see output in browser.

---

### Example 2 — Output in Console (Node.js)

**`src/index.ts`**
```typescript
var username: string = "John";
console.log("Hello! " + username);
```

**Steps:**
1. Transcompile:
   ```bash
   tsc index.ts
   ```
2. Run using Node:
   ```bash
   node index.js
   ```

---

## 4. TypeScript Variables

> Variables are **storage locations in memory** where you can store a value and use it as part of any expression.

### Variable Configuration — 3 Phases

| Phase | Description | Example |
|-------|-------------|---------|
| **Declaration** | Reserve memory, no value assigned | `var x;` |
| **Assignment** | Assign a value to a declared variable | `x = 10;` |
| **Initialization** | Declare and assign in a single step | `var y = 20;` |

```typescript
var x;       // Declaration
x = 10;      // Assignment
var y = 20;  // Initialization
y = 30;      // Assignment (updating value)
```

---

### Variable Keywords in TypeScript

TypeScript supports three keywords for declaring variables:

1. `var`
2. `let`
3. `const`

---

### `var`

- Defines a **function-scoped** variable
- Can be declared in any block inside a function and accessed from any other block in the same function
- Allows **declaring**, **assignment**, and **initialization**

```typescript
function Demo() {
  var x;
  x = 10;
  if (x == 10) {
    var y = 20;
  }
  console.log("X= " + x + "\n" + "Y= " + y);
}
Demo();
// Output:
// X= 10
// Y= 20
```

#### Shadowing with `var`

> **Shadowing** is the process of re-declaring or re-initializing a variable within the same scope.

- `var` **allows** shadowing

```typescript
function Demo() {
  var x;
  x = 10;
  if (x == 10) {
    var y = 20;
    var y = 30; // ✅ Shadowing allowed with var
  }
  console.log("X= " + x + "\n" + "Y= " + y);
}
Demo();
```

#### Hoisting with `var`

> **Hoisting** allows the compiler to access a variable declaration from anywhere in its scope, regardless of where it was written.

- `var` **allows** hoisting — there is no required order for declaring and using a variable.

```typescript
function Demo() {
  x = 10;
  console.log("X= " + x); // ✅ Works fine
  var x;                   // Declaration comes after use
}

// Also valid outside a function:
x = 10;
console.log("X= " + x);
var x;
```

---

### `let`

- Defines a **block-scoped** variable
- Accessible only within the block where it is defined, and its inner blocks
- Allows **declaring**, **assignment**, and **initialization**
- Does **NOT** allow shadowing
- Does **NOT** allow hoisting

```typescript
function Demo() {
  let x;
  x = 10;
  if (x == 10) {
    let y = 20;
    y = 30; // ✅ Reassignment is allowed
  }
  console.log("x= " + x + " y= " + y); // ❌ Error: Cannot find name 'y'
}
Demo();
```

```typescript
let y = 20;
var y = 30; // ❌ Error: Shadowing not allowed with let
```

---

### `const`

- Also **block-scoped**
- Allows **only initialization** — declaration alone or assignment after declaration is **not** allowed
- Does **NOT** allow shadowing
- Does **NOT** allow hoisting

```typescript
const x;       // ❌ Invalid — must be initialized at declaration
x = 10;        // ❌ Invalid — cannot assign after separate declaration
const x = 10;  // ✅ Valid — initialization
x = 20;        // ❌ Invalid — cannot reassign a const
```

---

### Variable Keywords — Quick Comparison

| Feature | `var` | `let` | `const` |
|---------|-------|-------|---------|
| Scope | Function | Block | Block |
| Declaration only | ✅ | ✅ | ❌ |
| Assignment | ✅ | ✅ | ❌ |
| Initialization | ✅ | ✅ | ✅ (required) |
| Shadowing | ✅ | ❌ | ❌ |
| Hoisting | ✅ | ❌ | ❌ |

---

*End of Day 01 Notes*