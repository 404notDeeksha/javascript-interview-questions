# 📘 Javascript Interview Questions & Answers

This repo is my personal collection of Javascript interview Q&A.  
Each question is answered briefly and clearly to help with interview prep and revision.

---

| No. | Question                                                                                                                 |
| --- | ------------------------------------------------------------------------------------------------------------------------ |
|     | BASICS                                                                                                                   |
| 1   | [What is JavaScript? What is role of js engine?](#what-is-javascript-what-is-role-of-js-engine)                          |
| 2   | [What are its features?](#what-are-its-features)                                                                         |
| 3   | [What is role of js engine?](#what-is-role-of-js-engine)                                                                 |
| 4   | [What are the different data types in JavaScript?](#what-are-the-different-data-types-in-javascript)                     |
| 5   | [What is Imperative & Declarative Programming in Javascript?](#what-is-imperative--declarative-programming-in-javascript) |
| 6   | [What is Client side Rendering & Server side Rendering?](#what-is-client-side-rendering--server-side-rendering)                                                                           |
| 7   | [What is scope in Js?](#what-is-scope-in-js)                                                                               |
| 8   | [What is difference between var, let & const?](#what-is-difference-between-var-let--const)                                                                                      |
| 9   | [What is Hoisting?](#what-is-hoisting)                                                                                    |
| 10  | [What are stages of Js Code processing?](#what-are-stages-of-js-code-processing)                                          |

1. ### What is javascript?
   Javascript is a programming language which is used to convert static web apps into interactive dynamic ones.

2. ### What are its features?

   It is _lightweight_ & _versatile_. <br/> It is a _dynamically typed language_ (data type of variable is decided at runtime).<br/> It is _single threaded_.<br/> It is _weakly typed_ (variable types are not enforced) & _interpreted language_.<br/> It is _Event Driven_, _asynchronous_, & has _Rich ecosystem_.

3. ### What is role of js engine?

   Js engine is a program in web browser which executes js code. In order to enable it, use js file under `<script>` tag in index.html file. <br/> Chrome - V8 <br/> Firefox - spiderMonkey <br/> Safari - Js core <br/> Edge - Chakra

4. ### What are the different data types in JavaScript?

   Javascript has basically 2 data types: <br/> <br/> A.**Primitive**: immutable, store single values:<br/> 1. **Number**: represents integers & floating-point numbers. eg: 7, 5.48. <br/> 2. **String**: represents sequence of characters. eg: "Hello".<br/> 3. **BigInt**: represents integers with arbitrary precision. number ends with n. Can represent any size of number, limited by memory. eg: 123456123456n <br/> 4. **Boolean**: represents logical values - true or false. <br/> 5. **Undefined**: variable that has been declared but isnt assigned a value. eg. let value; <br/> 6. **Null**: represents _Intentional_ absence of any object value. eg: let value = null; <br/> 7. **Symbol**: represent unique , immutable values, often used as object property keys.<br/><br/> B. **Non-Primitive** : <br/>**Object**: Used to store collection of data & more complex entities. eg: Objects(key-value pairs), Arrays(ordered collections), Functions, Dates, Maps, Sets, Regular Expressions(RegExp) etc.

5. ### What is Imperative & Declarative Programming in Javascript?

    **Imperative** : This style of programming gives step by step instructions for how to achieve goals. main focus is on sequence of operations & control flow.<br/>eg: C, Python, Java, DSA use this approach.<br/><br/> `let results = [];`<br/>`for (let num of collection) {`<br/>    `if (num % 2 !== 0) {`<br/>    `results.push(num);`<br/>`}`<br/>`}`<br/><br/> **Declarative**:  This style of programming focuses on desired outcome & letting system decide how to do it. <br/> eg: SQL, HTML< React's JSX use this format.<br/><br/> `let results = collection.filter(num => num % 2 !== 0);`<br/>

6. ### What is Client side Rendering & Server side Rendering?  

   In *Client Side Rendering*, *browser* is responsible for rendering the web page. The server sends a basic HTML File & a Js bundle (after site has been deployed on a server). Browser runs the Js bundle which generates & displays UI. After Initial load, all updates & navigation happen in browser using Js. without reloading entire page. <br/><ul><li> It reduces Server load, as server mainly handles API/ data requests & not page rendering. <li> It leads to Interactive , dynamic user Experience, smoother navigation & real time updates.<li>It also means slower initial load times, because browser needs to download & exceute Js before showing content & SEO Challenges as search engines may find indexing content difficult on client-side.</ul> <br/><br/>In *Server Side Rendering*, the server *generates the complete HTML for each page* and sends it to the browser. The browser *displays the page immediately*, and then JavaScript can take over for further interactivity. <br/> For each new page request, server renders React Component into HTML which is then sended over to client. Browser displays this HTML & React *hydrates* it to make it interactive. <ul><li> This means *faster Initial load times*, as browser recieves ready- to - go HTML.  <li> It means *SEO optimisation* as search engines can index pre-rendered content. <li> Better experience on slow networks as browser does less work here. <li> It also means, *Slower Navigation* as each new page needs a round trip to server, more server resources & more complex development & deployment.</ul><br/><br/> Note: **Hydration** is only used with SSR. In this, when HTML from server is loaded by browser on client side, React *matches it with its V-DOM*, attaches *event handlers & listeners* to existing HTML elements & *takes over DOM management* from here onwards. It brings interactivity & performance in SSR apps as full UI re-render is not needed & SEO optimisation also takes place.

7. ### What is scope in Js?

   Scope means *current context* of *execution in which variables, objects & functions* are *accessible* in the code. <br/> <ol><li> **Global scope**: Variables declared outside of any function or block are in global scope. They can be accessed from anywhere. <li> **Function (Local) Scope**: Variables declared inside a function are only accessible within that function. They cannot be accessed from anywhere outside the function.<br/> Variables declared with var data type are function scoped. <li> **Block Scope**: Introduced in ES6, Variables declared with let and const inside a block (eg., within {}, for loops, if statements, etc.) are only accessible within that block. <li> Module Scope: While using Js modules, variables declared inside a module are only accessible within that module unless explicitly exported.</ol><br/> Note: <ul><li>Scopes work in hierarchy. Inner(child) scopes can access Outer(Parent) scope, not vice versa. <li> Variable Shadowing: Variables under same name can be declared under different scopes. </ul><br/> `let x = 1; // Global scope` <br/><br/> `function exampleFunction() {`      <br/> 
   `let x = 2; // Function scope` <br/> 
    `if (true) {` <br/>
        `let x = 3; // Block scope` <br/> 
           `console.log(x); // 3` <br/>
             `}` <br/>
  `console.log(x); // 2` <br/>
  `}` <br/><br/>`exampleFunction();` <br/>
  `console.log(x); // 1` <br/>

8. ### What is difference between var, let & const?

   | Feature         | var                                | let                                   | const                                      |
   |-----------------|------------------------------------|---------------------------------------|--------------------------------------------|
   | Scope           | Function-scoped or global-scoped   | Block-scoped                          | Block-scoped                               |
   | Hoisting        | Yes (initialized as `undefined` at top of its scope)   | Yes (but not initialized, Reference Err due to "temporal dead zone" (TDZ) applies)| Yes (but not initialized, TDZ applies)     |
   | Redeclaration   | Allowed within the same scope      | Not allowed in the same scope         | Not allowed in the same scope              |
   | Reassignment    | Allowed                            | Allowed                               | Not allowed (value is constant)            |
   | Initialization  | Optional                           | Optional                              | Required                                   |
   | Use Case        | Legacy code, old browsers          | Modern JS, variables that change      | Constants, values that never change        |
   
   **Hoisting** <br/>
   **var**: <br/> It is an implicit(default) keyword.<br/>
   `console.log(a); // Output: undefined`<br/>
   `var a = 10; // or a=10;`<br/>
   `console.log(a); // Output: 10`<br/><br/>
   **let**: <br/>
   `console.log(b); // ReferenceError: Cannot access 'b' before initialization`<br/>
   `let b = 20;`<br/>
   `console.log(b); // This line won't run`<br/><br/>
   **const**: <br/>
   `console.log(c); // ReferenceError: Cannot access 'c' before initialization` <br/>
   `const c = 30;`<br/>
   `console.log(c); // This line won't run`<br/>

   Tricky Question: 
   ```js
   for (var i = 0; i < 3; i++) {
   setTimeout(() => console.log(i), 1);
   }

   for (let i = 0; i < 3; i++) {
   setTimeout(() => console.log(i), 1);
   }
   //Output 333 012
   ```

9. ### What is Hoisting?

   Hoisting is a *Js mechanism* where interpreter appears to *move declarations of variables, functions, classes or imports* to the *top of their scope* before code is executed. <ul> <li>It means certain variables, functions can be accessed before they are actually declared in code. <li>**Variable Declarations** : Only declarations are hoisted & not initializations. <li> **Function Declarations**: These are fully hoisted, both function's name & body are available throughout the scope where they are declared.<li> **Class Declarations**: They are hoisted but not initialized, so referencing them before their declaration causes a ReferenceError.</ul><br/> Note: Hoisted means the code runs well at that point of flow (mostly declarations- let,var,const). <br/> It makes code more flexible & readable.  <br/> <br/> **Function Hoisting**:
   ```js 
   foo(); // "Hello"
   function foo() {
   console.log("Hello");
   }
   ``` 

10. ### What are stages of Js Code processing?

      Stages are: <br/> <ol> <li> **Parsing**: Js engine first parses the code (it reads Js source code, & checks for syntax errors. It converts code into structured format (DSA) called Abstract Syntax Tree (AST)). Parsing ensures code is valid for further processing. <li> **Compilation/Interpretation** : modern Js engines use mix of JIT compilation & interpretation. Engine converts parsed code into machine code/ bytecode which computer can execute. This step involves optimisation for faster execution. <li> **Execution Context Creation**: Before running the code, the engine creates an execution context. This is an environment where the code will run, including memory for variables and functions. It is of 2 main types: <br/> <ol> <li> 1. **Global Execution Context** (for code outside functions). <li> 2. **Function Execution Context** (created each time a function is called).</ol> <li> **Memory Allocation (Creation Phase)** : In each execution context, the engine performs a memory allocation phase (also called the "creation phase"). It sets up the variable environment, allocating space for variables and functions, and hoisting declarations as needed.  <li> **Code Execution (Execution Phase)** : The engine then executes the code line by line. It assigns values to variables, evaluates expressions, and runs function calls. <li> **Call Stack Management**: As functions are called, execution contexts are pushed onto the call stack (since Js is single threaded language). When a function finishes, its context is popped off the stack. <li> **Handling Asynchronous Code (Event Loop)**: For asynchronous operations (like setTimeout, Promises, AJAX), the engine interacts with the browser’s Web APIs, callback queue, and microtask queue.The event loop ensures that asynchronous callbacks are executed when the call stack is empty. </ol>

11. ###   
