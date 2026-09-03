# JAVASCRIPT (Zero → Advanced)

Format: Concept → Explanation → Syntax → Example → Practical Use → Common Mistake

## 🟢 FUNDAMENTALS

### 🔴 JavaScript kya hai
Programming language jo webpage ko interactive banati hai (logic, behavior, dynamic content).

### 🔴 Variables — var, let, const
```js
var a = 10;    // old way, function-scoped, avoid karo
let b = 20;    // block-scoped, value change ho sakti hai
const c = 30;  // block-scoped, value fix rehti hai
```
**Important:** `const` default use karo, jab value change karni ho tabhi `let` use karo. `var` modern JS me avoid karo.
**Common Mistake:** `const` object/array ko reassign nahi kar sakte, but unke andar ke values change kar sakte hain.

### 🔴 Data Types
```js
let str = "hello";       // String
let num = 42;             // Number
let bool = true;           // Boolean
let empty = null;          // null - intentional empty
let notDefined;             // undefined - value assign nahi hui
let big = 123n;              // BigInt
let sym = Symbol("id");       // Symbol - unique value
let obj = { name: "Rahul" };   // Object
```
**Important:** `typeof null` galti se `"object"` return karta hai (JS ka famous bug).

### 🔴 Operators
```js
// Arithmetic
5 + 3, 5 - 3, 5 * 3, 5 / 3, 5 % 3, 5 ** 2

// Comparison
5 == "5"    // true (type coerce karta hai) - AVOID
5 === "5"   // false (strict, type bhi check karta hai) - USE THIS

// Logical
&&, ||, !

// Ternary
let result = age >= 18 ? "Adult" : "Minor";

// Optional chaining
user?.address?.city   // agar user ya address undefined ho to error nahi, undefined return karega

// Nullish coalescing
let name = userName ?? "Guest"; // sirf null/undefined pe fallback deta hai (0 ya "" pe nahi)
```
**MUST KNOW:** `==` vs `===` — hamesha `===` use karo, type coercion bugs se bachne ke liye.

**Practice:** 5 variables banao different types ke, `===` aur `==` ka difference test karo console me.

---

## 🟢 CONTROL FLOW

### 🔴 if/else, switch
```js
if (age >= 18) {
  console.log("Adult");
} else if (age >= 13) {
  console.log("Teen");
} else {
  console.log("Child");
}

switch(day) {
  case "Mon": console.log("Monday"); break;
  default: console.log("Other day");
}
```

### 🔴 Loops
```js
for (let i = 0; i < 5; i++) { console.log(i); }
while (condition) { }
do { } while (condition);

for (const item of array) { }     // values ke liye
for (const key in object) { }     // keys ke liye
```
**Common Mistake:** `for...in` ko arrays pe use karna (use objects ke liye hai, arrays ke liye `for...of` ya `.forEach`)

**Practice:** 1-100 tak sirf even numbers print karo loop se. Ek array ko `for...of` se loop karo.

---

## 🟢 FUNCTIONS — MUST KNOW

```js
// Function Declaration
function greet(name) {
  return `Hello ${name}`;
}

// Function Expression
const greet2 = function(name) {
  return `Hello ${name}`;
};

// Arrow Function
const greet3 = (name) => `Hello ${name}`;

// Default parameters
function greet4(name = "Guest") { return `Hi ${name}`; }

// Rest parameters
function sum(...numbers) {
  return numbers.reduce((a, b) => a + b, 0);
}
```

### 🔴 Callback Functions & Higher-Order Functions
**What is it?** Function jo doosre function ko argument ke roop me leta hai ya return karta hai.
```js
function processUser(name, callback) {
  console.log("Processing " + name);
  callback();
}
processUser("Rahul", () => console.log("Done!"));
```
**Practical Use:** `setTimeout`, array methods (`map`, `filter`) sab callbacks use karte hain.

**Common Mistake:** Arrow functions me `this` different behave karta hai regular functions se — arrow function apna `this` nahi banata, parent scope se leta hai.

**Practice:** Ek function banao jo array leke usko double karke return kare. Ek callback-based function banao.

---

## 🟢 ARRAYS — MUST KNOW

```js
let arr = [1, 2, 3, 4, 5];
```

| Method | Kaam | Modifies Original? |
|---|---|---|
| `push(x)` | end me add | ✅ Yes |
| `pop()` | end se remove | ✅ Yes |
| `shift()` | start se remove | ✅ Yes |
| `unshift(x)` | start me add | ✅ Yes |
| `splice()` | add/remove kahi bhi | ✅ Yes |
| `sort()` | sort karta hai | ✅ Yes |
| `slice(start,end)` | part nikalta hai | ❌ No (new array) |
| `concat()` | arrays jodta hai | ❌ No (new array) |
| `map()` | transform karke new array deta hai | ❌ No |
| `filter()` | condition ke hisab se new array deta hai | ❌ No |
| `find()` | pehla matching element | ❌ No |
| `findIndex()` | pehla matching index | ❌ No |
| `includes()` | value hai ya nahi (true/false) | ❌ No |
| `indexOf()` | value ka index | ❌ No |
| `forEach()` | har element pe loop (kuch return nahi karta) | ❌ No |
| `reduce()` | array ko single value me convert karta hai | ❌ No |
| `some()` | kam se kam ek condition match kare | ❌ No |
| `every()` | sab condition match karein | ❌ No |

**🔴 IMPORTANT: `map` vs `forEach`**
```js
const doubled = [1,2,3].map(n => n * 2);   // returns [2,4,6] - naya array
[1,2,3].forEach(n => console.log(n));       // kuch return nahi karta, sirf loop
```

**🔴 IMPORTANT: `reduce` example**
```js
const total = [10, 20, 30].reduce((acc, curr) => acc + curr, 0);
// acc = accumulator (running total), curr = current item, 0 = starting value
console.log(total); // 60
```

**Common Mistake:** `map` ka result use na karna (map hamesha new array return karta hai, use store karna zaroori hai).

**Practice:**
1. Array of numbers ko `filter` se sirf even numbers nikalo
2. `map` se array ke saare items ko square karo
3. `reduce` se total sum nikalo
4. `find` se specific object array me dhundo

---

## 🟢 OBJECTS — MUST KNOW

```js
const user = {
  name: "Rahul",
  age: 25,
  address: { city: "Jaipur" },
  greet() { return `Hi, I'm ${this.name}`; }
};

// Destructuring
const { name, age } = user;

// Spread
const updatedUser = { ...user, age: 26 };

// Optional chaining
console.log(user?.address?.pincode); // undefined agar nahi hoga, error nahi dega
```
**Important:** `this` object ke andar current object ko refer karta hai (jab regular function use ho, arrow function me nahi).

**Practice:** Ek `student` object banao (name, marks, subjects array). Destructure karo. Spread se copy banao with ek field change karke.

---

## 🔵 IMPORTANT JS CONCEPTS (ADVANCED)

### 🔴 Scope
```js
let globalVar = "I'm global";

function test() {
  let functionVar = "I'm function scoped";
  if (true) {
    let blockVar = "I'm block scoped"; // sirf is {} ke andar accessible
  }
}
```
- **Global scope** → kahi bhi accessible
- **Function scope** → sirf function ke andar (`var` follow karta hai)
- **Block scope** → sirf `{ }` ke andar (`let`/`const` follow karte hain)

### 🔴 Hoisting & Temporal Dead Zone
**What is it?** JS variable/function declarations ko memory me pehle se "upar utha" leta hai execution se pehle.
```js
console.log(x); // undefined (hoisted but not initialized)
var x = 5;

console.log(y); // ReferenceError - Temporal Dead Zone
let y = 5;
```
**Important:** `var` hoisted hoke `undefined` deta hai, `let`/`const` hoisted hote hain but access karne pe error (TDZ) deta hai.

### 🔴 Closures — MUST KNOW (Interview Favorite)
**What is it?** Function jo apne outer function ke variables ko yaad rakhta hai, chahe outer function execute ho chuka ho.
```js
function counter() {
  let count = 0;
  return function() {
    count++;
    return count;
  };
}
const increment = counter();
console.log(increment()); // 1
console.log(increment()); // 2
```
**Practical Use:** Private variables banane ke liye, data hiding, ek baar setup karke reuse karna (e.g. event handlers me state maintain karna).

### 🔴 this, call, apply, bind
```js
const person = { name: "Rahul" };
function greet() { console.log(`Hi ${this.name}`); }

greet.call(person);              // Hi Rahul
greet.apply(person);              // Hi Rahul (args array me lete hain)
const boundGreet = greet.bind(person);
boundGreet();                      // Hi Rahul
```
**Difference:** `call`/`apply` turant invoke karte hain, `bind` naya function return karta hai jo baad me call ho sakta hai.

### 🔵 Execution Context, Call Stack, Event Loop
**What is it?** JS single-threaded hai — ek time pe ek kaam karta hai. Call stack functions ko track karta hai. Event Loop async code (setTimeout, promises) ko manage karta hai taaki main thread block na ho.
**Practical relevance:** Ye samajhna zaroori hai ki `setTimeout(fn, 0)` bhi turant execute nahi hota — pehle call stack khali hota hai.

### 🔵 Prototypes & Prototype Chain
**What is it?** Har JS object ek doosre object (`prototype`) se linked hota hai jaha se wo properties/methods "inherit" karta hai.
```js
console.log([1,2,3].__proto__ === Array.prototype); // true
```

### 🔴 Classes & Inheritance
```js
class Animal {
  constructor(name) { this.name = name; }
  speak() { return `${this.name} makes a sound`; }
}
class Dog extends Animal {
  speak() { return `${this.name} barks`; }
}
const d = new Dog("Tommy");
console.log(d.speak()); // Tommy barks
```

### 🔴 Modules (import/export)
```js
// math.js
export const add = (a, b) => a + b;
export default function multiply(a, b) { return a * b; }

// main.js
import multiply, { add } from './math.js';
```
**Practical Use:** Code ko files me split karke organize karna — React/Node projects me hamesha use hota hai.

**Practice (Advanced):**
1. Ek closure banao jo bank balance track kare (deposit/withdraw functions ke saath)
2. `call`/`bind` use karke ek function ko different object ke context me run karo
3. Ek `Class` banao (e.g. `Car`) with constructor aur method, phir usse inherit karke `SportsCar` class banao

---

## Quick Revision
Variables (`let`/`const`) → Data types → Functions (arrow) → Arrays (map/filter/reduce) → Objects (destructuring/spread) → Closures → `this` → Classes → Modules

## Cheat Sheet
```js
const arr = [1,2,3];
arr.map(x => x*2);
arr.filter(x => x>1);
arr.reduce((a,b) => a+b, 0);

const {a, b} = obj;
const newObj = {...obj, key: value};

const fn = (x) => x * 2;
```

## Must Remember
- `===` always use karo, `==` avoid karo
- `map/filter/reduce` original array modify nahi karte
- `const` default, `let` jab value change ho, `var` avoid
- Closures = function + remembered outer scope
- Arrow functions apna `this` nahi rakhte

## Common Mistakes
- `map()` ka return value ignore karna
- `this` ko arrow function me galat expect karna
- `==` use karna `===` ki jagah
- Array ko `for...in` se loop karna

## Interview Questions
1. `let`, `const`, `var` me difference?
2. Closure kya hai, example do
3. `map` vs `forEach` vs `filter`?
4. Hoisting kya hai?
5. `this` kaise decide hota hai?
6. Event loop kaise kaam karta hai?

## Practice Tasks
**Beginner:** Variables, loops, basic functions
**Intermediate:** Array methods (map/filter/reduce) pe 10 chhote tasks
**Advanced:** Closures, classes, prototype chain samajhna aur implement karna

## ✍️ Notebook Notes
1. `let`/`const` block scoped, `var` function scoped (avoid)
2. `===` strict equality — hamesha use karo
3. Arrow function: `(param) => expression`
4. `map/filter/reduce` = new array return karte hain (original untouched)
5. `push/pop/splice/sort` = original array modify karte hain
6. Destructuring: `const {a,b} = obj` | Spread: `{...obj}`
7. Closure = inner function + outer variables ki memory
8. `this` normal function me caller decide karta hai, arrow function me parent se milta hai
9. `call/apply/bind` = function ka `this` manually set karna
10. Module: `export` / `import`
