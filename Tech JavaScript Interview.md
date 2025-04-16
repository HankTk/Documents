# JavaScript Interview Questions & Answers (Quick Reference)

---

## 1. Basic Questions

- **What's the difference between `var`, `let`, and `const`?**  
  → `var`: function-scoped, `let`/`const`: block-scoped, `const`: can't be reassigned.

- **Difference between `==` and `===`?**  
  → `==`: loose equality (type conversion), `===`: strict equality (no conversion).

- **Difference between `null` and `undefined`?**  
  → `null`: intentional absence of value, `undefined`: variable declared but not assigned.

- **Surprising result of `typeof`?**  
  → `typeof null // "object"` (historical bug).

---

## 2. Functions & Scope

- **Types of scope in JavaScript?**  
  → Global, function, and block scope.

- **What is a closure?**  
  → A function that retains access to its outer lexical scope.

- **How is `this` determined?**  
  → Depends on how a function is called. Arrow functions inherit `this`.

- **Arrow function differences?**  
  → No `this`, no `arguments`, shorter syntax.

---

## 3. Asynchronous JavaScript

- **Difference: `setTimeout` vs `setInterval`**  
  → `setTimeout`: runs once after delay, `setInterval`: repeats.

- **States of a Promise?**  
  → `pending`, `fulfilled`, `rejected`.

- **How does `async/await` work?**  
  → Syntactic sugar for handling Promises in a cleaner way.

- **How to handle errors in `fetch`?**  
  → Use `.catch()` or `try/catch` with `async/await`.

---

## 4. Objects & Classes

- **What is the prototype chain?**  
  → Object inheritance chain via `__proto__`.

- **Class vs constructor function?**  
  → `class` is syntactic sugar over constructor functions.

- **Use of `Object.create`?**  
  → Creates a new object with specified prototype.

- **What are getters and setters?**  
  → Special methods for property access and assignment.

---

## 5. Events & DOM

- **Phases of event propagation?**  
  → Capturing → Target → Bubbling.

- **What does `once` option do in `addEventListener`?**  
  → Automatically removes listener after first call.

- **`preventDefault()` vs `stopPropagation()`**  
  → Prevent default behavior vs stop bubbling/capturing.

- **What is the virtual DOM?**  
  → Lightweight in-memory DOM for efficient updates.

---

## 6. ES6+ Features

- **Block scope with `let`/`const`?**  
  → Variables exist only within `{}` blocks.

- **What is the spread operator (`...`) used for?**  
  → To expand arrays or objects.

- **Difference between `Map` and `Set`?**  
  → `Map`: key/value pairs, `Set`: unique values.

- **Advantages of `WeakMap` / `WeakSet`?**  
  → Keys are garbage-collectable, prevents memory leaks.

---

## 7. Performance & Optimization

- **`debounce` vs `throttle`?**  
  → `debounce`: delay execution until pause, `throttle`: limit to interval.

- **`localStorage` vs `sessionStorage` vs `cookie`?**  
  → `local`: persists, `session`: per tab, `cookie`: sent with requests.

- **Use of `requestAnimationFrame`?**  
  → For smooth animations synced to display refresh.

- **Causes and prevention of memory leaks?**  
  → Unremoved references or event listeners; always clean up.

---

## 8. Security

- **What is CORS?**  
  → Mechanism to control cross-origin requests.

- **What is XSS?**  
  → Injection of malicious scripts into web pages.

- **How to prevent CSRF?**  
  → Use tokens, set `SameSite` cookie attribute.

- **Why is `eval()` dangerous?**  
  → Executes arbitrary code; high security and performance risks.

---