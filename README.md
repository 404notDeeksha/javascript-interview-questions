# 📘 Javascript Interview Questions & Answers

This repo is my personal collection of Javascript interview Q&A.  
Each question is answered briefly and clearly to help with interview prep and revision.

### Table of Contents

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
| 11  | [What is JSON?](#what-is-json)|
| 12  | [What is typeof operator in Js?](#what-is-typeof-operator-in-js) |
| 13  | [What is Type Casting & Type Coercion?](#what-is-type-casting--type-coercion) |
| 14  | [What is Concatenation?](#what-is-concatenation) |
| 15  | [What are Operators in js?](#what-are-operators-in-js) |
| 16   | [What is Short Circuit Evaluation In js?](#what-is-short-circuit-evaluation-in-js) |
| 17  | [What are Spread & Rest Operators?](#what-are-spread--rest-operators) |
| 18  | [What is Loose Equality & Strict Equality Operators in Js?](#what-is-loose-equality--strict-equality-operators-in-js) |
|     |   FUNCTIONS                                                                                                                                |
| 19  | [What are Functions? What are ways to define them?](#what-are-functions-what-are-ways-to-define-them) |
| 20  | [What is a Callback Function?](#what-is-a-callback-function) |
| 21  | [What are Higher Order Functions(HOCs)?](#what-are-higher-order-functions(hocs)) |
| 22  | [What are Closures?](#what-are-closures) |
| 23   | [What are Objects in JS? What are ways to create it?](#what-are-operators-in-js) |
| 24   | [What is Object Prototype?](#what-is-object-prototype) |
| 25   | [What is Prototypal Inheritance?](#what-is-prototypal-inheritance) |
| 26   | [What are Indexed Collections in React?](#what-are-indexed-collections-in-react) |
| 27 | [What are Arrays in Js? What are its methods?](#what-are-arrays-in-js-what-are-its-methods) |
| 28 | [How reduce method works?](#how-reduce-method-works) |
| 29 | [What are Array like Objects in Js?](#what-are-array-like-objects-in-js) |
| 30 | [What are JavaScript Loops?](#what-are-javascript-loops) |
| 31 | [What is Lexical Scoping in Js?](#what-is-lexical-scoping-in-js) |
<!--| 32 | [](#) |
| 33 | [](#) |
| 34 | [](#) |
| 35 | [](#) | -->


1. ### What is javascript?
   Javascript is a programming language which is used to convert static web apps into interactive dynamic ones.

2. ### What are its features?

   It is _lightweight_ & _versatile_. <br/> It is a _dynamically typed language_ (data type of variable is decided at runtime).<br/> It is _single threaded_.<br/> It is _weakly typed_ (variable types are not enforced) & _interpreted language_.<br/> It is _Event Driven_, _asynchronous_, & has _Rich ecosystem_.

3. ### What is role of js engine?

   Js engine is a program in web browser which **executes** js code. In order to enable it, use js file under `<script>` tag in index.html file. <br/> Chrome - V8 <br/> Firefox - spiderMonkey <br/> Safari - Js core <br/> Edge - Chakra

4. ### What are the different data types in JavaScript?

   Javascript has basically 2 data types: <br/> <br/> A.**Primitive**: immutable, store single values:<br/> 1. **Number**: represents integers & floating-point numbers. eg: 7, 5.48. <br/> 2. **String**: represents sequence of characters. eg: "Hello".<br/> 3. **BigInt**: represents integers with arbitrary precision. number ends with n. Can represent any size of number, limited by memory. eg: 123456123456n <br/> 4. **Boolean**: represents logical values - true or false. <br/> 5. **Undefined**: variable that has been declared but isnt assigned a value. eg. let value; <br/> 6. **Null**: represents _Intentional_ absence of any object value. eg: let value = null; <br/> 7. **Symbol**: represent unique , immutable values, often used as object property keys.<br/><br/> B. **Non-Primitive** : <br/>**Object**: They are mutable, are used to store collection of data & more complex entities. eg: Objects(key-value pairs), Arrays(ordered collections), Functions, Dates, Maps, Sets, Regular Expressions(RegExp) etc.
   > They store value & hold reference to a memory location. 
   
   Tricky Question:
   ```js
   let x = { a: 1 };  // x points to object1 in memory
   let y = x;         // y also points to object1
   x = { b: 2 };      // x now points to object2; y still points to previous reference of x, object1 (Reassignment)


   let x = { a: 1 };  // x points to object1 in memory
   let y = x;         // y also points to object1
   x.a = 2;      // Mutation. This changes x & thus y too. 
   ```

   **[⬆ Back to Top](#table-of-contents)**

5. ### What is Imperative & Declarative Programming in Javascript?

    **Imperative** : This style of programming gives step by step instructions for how to achieve goals. main focus is on *sequence of operations & control flow*.<br/>eg: C, Python, Java, DSA use this approach.<br/><br/> `let results = [];`<br/>`for (let num of collection) {`<br/>    `if (num % 2 !== 0) {`<br/>    `results.push(num);`<br/>`}`<br/>`}`<br/><br/> **Declarative**:  This style of programming focuses on desired outcome & letting system decide how to do it. <br/> eg: SQL, HTML, React's JSX use this format.<br/> `let results = collection.filter(num => num % 2 !== 0);`<br/>

   **[⬆ Back to Top](#table-of-contents)**    

6. ### What is Client side Rendering & Server side Rendering?  

   In *Client Side Rendering*, *browser* is responsible for rendering the web page. The server sends a basic HTML File & a Js bundle (after site has been deployed on a server). Browser runs the Js bundle which generates & displays UI. After Initial load, all updates & navigation happen in browser using Js. without reloading entire page. <br/><ul><li> It reduces Server load, as server mainly handles API/ data requests & not page rendering. <li> It leads to Interactive , dynamic user Experience, smoother navigation & real time updates.<li>It also means slower initial load times, because browser needs to download & execute Js before showing content & SEO Challenges as search engines may find indexing content difficult on client-side.</ul> <br/><br/>In *Server Side Rendering*, the server *generates the complete HTML for each page* and sends it to the browser. The browser *displays the page immediately*, and then JavaScript can take over for further interactivity. <br/> For each new page request, server renders React Component into HTML which is then sended over to client. Browser displays this HTML & React *hydrates* it to make it interactive. <ul><li> This means *faster Initial load times*, as browser recieves ready-to-go HTML.  <li> It means *SEO optimisation* as search engines can index pre-rendered content. <li> Better experience on slow networks as browser does less work here. <li> It also means, *Slower Navigation* as each new page needs a round trip to server, more server resources & more complex development & deployment.</ul>
   > **Hydration** is only used with SSR. In this, when HTML from server is loaded by browser on client side, React *matches it with its V-DOM*, attaches *event handlers & listeners* to existing HTML elements & *takes over DOM management* from here onwards. It brings *interactivity & performance* in SSR apps as full UI re-render is not needed & SEO optimisation also takes place.

   **[⬆ Back to Top](#table-of-contents)**   

7. ### What is scope in Js?

   Scope means *current context* of *execution in which variables, objects & functions* are *accessible* in the code. <br/> <ol><li> **Global scope**: Variables declared outside of any function or block are in global scope. They can be accessed from anywhere. <li> **Function (Local) Scope**: Variables declared inside a function are only accessible within that function. They cannot be accessed from anywhere outside the function.<br/> Variables declared with var data type are function scoped. <li> **Block Scope**: Introduced in ES6, Variables declared with let and const inside a block (eg., within {}, for loops, if statements, etc.) are only accessible within that block. <li> Module Scope: While using Js modules, variables declared inside a module are only accessible within that module unless explicitly exported.</ol>
   > Scopes work in hierarchy. Inner(child) scopes can access Outer(Parent) scope, not vice versa.
   Variable Shadowing: Variables under same name can be declared under different scopes. 
   
   ```js
   let x = 1;  // Global scope

   function exampleFunction() {
      let x = 2; // Function scope 
      if (true) {
        let x = 3; // Block scope 
          console.log(x); // 3
         }
      console.log(x); // 2
   }
   exampleFunction();
   console.log(x); // 1
   ```

   **[⬆ Back to Top](#table-of-contents)**  

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
   **var**: <br/> It is an implicit (default) keyword.<br/>
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

   **[⬆ Back to Top](#table-of-contents)**   

9. ### What is Hoisting?

   Hoisting is a *Js mechanism* where interpreter appears to *move declarations of variables, functions, classes or imports* to the *top of their scope* before code is executed. <ul> <li>It means certain variables, functions can be accessed before they are actually declared in code.  <li>**Variable Declarations** : Only declarations are hoisted & not initializations. <li> **Function Declarations**: These are fully hoisted, both function's name & body are available throughout the scope where they are declared.<li> **Class Declarations**: They are hoisted but not initialized, so referencing them before their declaration causes a ReferenceError.</ul> <br/> **Function Hoisting**:
   ```js 
   foo(); // "Hello"
   function foo() {
   console.log("Hello");
   }
   ``` 
   > Hoisted means the code runs well at that point of flow (mostly declarations- let,var,const). 
   It makes code more flexible & readable. 
   When variables are declared, memory is assigned to them at top of their scope (Memory allocation phase). 
   var gets undefined & let,const 's memory cant be used, thus Temporal Dead Zone.

   Tricky Question:
   ```js
   function sayHi() {
   console.log(name);
   console.log(age);
   var name = 'Deeksha';
   let age = 29;
   }

   sayHi();
   //Output undefined Reference Error
   ```
   **[⬆ Back to Top](#table-of-contents)**

10. ### What are stages of Js Code processing?

      Stages are: <br/> <ol> <li> **Parsing**: Js engine first parses the code (it reads Js source code, & checks for syntax errors. It converts code into structured format (DSA) called Abstract Syntax Tree (AST)). Parsing ensures code is valid for further processing. <li> **Compilation/Interpretation** : modern Js engines use mix of JIT (Just-in-time) compilation & interpretation. Engine converts parsed code into machine code/ bytecode which computer can execute. This step involves optimisation for faster execution. <li> **Execution Context Creation**: Before running the code, the engine creates an execution context. This is an environment where the code will run, including memory for variables and functions. It is of 2 main types: <br/> <ol> <li> 1. **Global Execution Context** (for code outside functions). <li> 2. **Function Execution Context** (created each time a function is called).</ol> <li> **Memory Allocation (Creation Phase)** : In each execution context, the engine performs a memory allocation phase (also called the "creation phase"). It sets up the variable environment, allocating space for variables and functions, and hoisting declarations as needed.  <li> **Code Execution (Execution Phase)** : The engine then executes the code line by line. It assigns values to variables, evaluates expressions, and runs function calls. <li> **Call Stack Management**: As functions are called, execution contexts are pushed onto the call stack (since Js is single threaded language). When a function finishes, its context is popped off the stack. <li> **Handling Asynchronous Code (Event Loop)**: For asynchronous operations (like setTimeout, Promises, AJAX), the engine interacts with the browser’s Web APIs, callback queue, and microtask queue.The event loop ensures that asynchronous callbacks are executed when the call stack is empty. </ol>

   **[⬆ Back to Top](#table-of-contents)**      

11. ### What is JSON?

      JSON stands for JavaScript Object Notation. It is a lightweight, text-based format used to store and transport data. JSON is easy for humans to read and write, and easy for machines to parse and generate. <br/>It is written as "key"-"value" pairs & is language independent.
      ```js
      {
      "name": "John",
      "age": 30,
      "car": null
      }
      ```

   **[⬆ Back to Top](#table-of-contents)**      

12. ### What is typeof operator in Js?

      It returns a string describing datatype of variable or value in picture. It is used for debugging, checking variables before performing operations.

      ```js
      typeof 42;           // "number"
      typeof "hello";      // "string"
      typeof true;         // "boolean"
      typeof undefined;    // "undefined"
      typeof {a:1};        // "object"
      typeof [1,2,3];      // "object"   // Arrays are also objects
      typeof null;         // "object"   // This is a known quirk in JavaScript
      typeof function(){}; // "function"
      ```
     > cant differentiate between arrays or Objects & null or Objects.
      isNaN() returns true for non number values-which cant convert to numbers. true for number values.
      isNaN('a')  //true
      isNaN(2)    //false

   **[⬆ Back to Top](#table-of-contents)**     

13. ### What is Type Casting & Type Coercion?

      These refer to changing value from one datatype to another in js.<br/>
      1. **Type Casting (Explicit Type Conversion)** : in this, user explicitly converts a value from one type to another using built-in functions or methods.

      ```js
      let num = "123";
      let convertedNum = Number(num); // Explicitly converts string to number
      Boolean(null);  // false
      Boolean(undefined) // false
      ```
      2.**Type Coercion (Implicit Type Conversion)**: here, js automatically converts a value from one type to another as needed, usually during operations or comparisons.<br/> Often done when using operators like +, ==, or conditional statements.

      ```js
      let result = "5" + 2; // JavaScript concatenates with + operator if either operand is string -> 2 to "2", result is "52"
      let isEqual = (5 == "5"); // JavaScript coerces "5" to 5, result is true
      console.log([] == ![]);         // true
      // [] is truthy, but ![] is false. 
      // [] == false → [] coerced to "", false to 0, 
      // "" == 0 → true[2].
      console.log('d'-0);  //NaN
      // 'd'->string to number but string => number not possible
      // Nan-0 = Nan
      ```

   **[⬆ Back to Top](#table-of-contents)**      

14. ### What is Concatenation?

      It is the process of joining two or more strings together to form a single, longer string. 
      >js concatenates with + operand if either operator is string. with -, * , / js tries to convert(direct) operands to numbers.
      ```js
      let message = "Hello";
      message += ", World!"; // "Hello, World!"
      let greet = "Good";
      let result = greet.concat(" Morning", " Everyone!"); // "Good Morning Everyone!"
      const words = ["I", "love", "coding"];
      const sentence = words.join(" "); // "I love coding"
      ```

   **[⬆ Back to Top](#table-of-contents)**   

15. ### What are Operators in js?

      | Operator Type           | Example(s)                                      | Description                                 |
      |------------------------|-------------------------------------------------|---------------------------------------------|
      | **Arithmetic**         | `+`, `-`, `*`, `/`, `%`, `++`, `--`, `**`       | Math operations (add, subtract, multiply, divide, etc.) |
      | **Assignment**         | `=`, `+=`, `-=`, `*=`, `/=`, `%=`, `**=`        | Assign or update variable values            |
      | **Comparison**         | `==`, `===`, `!=`, `!==`, `>`, `<`, `>=`, `<=`  | Compare values and types                    |
      | **Logical**            | `&&`, `!`,`Logical OR operator`, `!`                                 | Combine or invert boolean values            |
      | **String**             | `+`, `+=`                                       | Join strings together                       |
      | **Bitwise**            | `&`,`^`, `~`, `<<`, `>>`, `>>>`, `Bitwise OR operator`     | Works at the binary (bit) level, on single operand             |
      | **Conditional (Ternary)** | `condition ? val1 : val2`                    | Short `if-else`                             |
      | **Type**               | `typeof`, `instanceof`                          | Check or test data types                    |
      | **Optional Chaining**       | `obj?.prop`, `arr?.[index]`, `func?.()`            | Safely access nested properties, array items, or call functions without throwing an error if an intermediate value is `null` or `undefined` |
      | **Nullish Coalescing**      | `a ?? b`                                           | Returns `a` if it's not `null` or `undefined`, otherwise returns `b` (useful for setting default values only when the left side is truly "missing") |

      ```js
      let number = 0;
      console.log(number++); //0 number=1 (i++ allows time to increment number later & executes code now)
      console.log(++number); //2 number=2 (++i doesnt allow time. it has to increment first, then execute code)
      console.log(number); //2 
      ```

   **[⬆ Back to Top](#table-of-contents)**      

16. ### What is Short Circuit Evaluation In js?

      It refers to how *logical operators* like **&& (AND),|| (OR)**, and newer operators such as **?? (nullish coalescing)** and **? (optional chaining)** evaluate expressions from **left to right** and **stop as soon as the result is determined**, without evaluating the rest of the expression

      1. Logical AND (&&): it evaluates left expression. If its true, it evaluates right expression. If its false, right expression is not evaluated.3
         ```js
         false && doSomething(); // doSomething() is NOT called
         ```
      2. LOGICAL OR (||) : it evaluates left expression. If its true, it doesnt goes further to right expression as whole statement is truthy. If its false, right expression is evaluated.
         ```js
         true || doSomething(); // doSomething() is NOT called
         ```
      > This skips evaluating parts of expressions & makes code faster

      **[⬆ Back to Top](#table-of-contents)**   

17. ### What are Spread & Rest Operators?

      **Spread Operator**: It "expands" an iterable (like an array or string) into its individual elements.<br/>
      It is commonly used in places where zero or more arguments or elements are expected, such as in **function calls, array literals, or object literals**.<br/>
      It creates a **shallow copy**. It creates a new memory.
      ```js
      //Function calls: passing array as function elements
      function sum(a, b, c) { return a + b + c; }

      const numbers = [1, 2, 3];
      sum(...numbers); // 6

      //Expanding Arrays:
      const arr = [1, 2, 3];
      const newArr = [...arr, 4, 5]; // [1, 2, 3, 4, 5]

      //Merging Objects:
      const obj1 = { a: 1 };
      const obj2 = { b: 2 };
      const merged = { ...obj1, ...obj2 }; // { a: 1, b: 2 }

      //Shallow copy:
      let object1 = { name: "Alice", age: 30 };
      let object2 = { ...object1 }; // New object in memory
      let object3 = object1;
      object1.name = "Bob"; //Mutation
      console.log(object1, object2, object3); // { name: 'Bob', age: 30 } { name: 'Alice', age: 30 } {name: 'Bob', age: 30}
      //object3 refers to same location as of object1
      ```

      **Rest Operators**: It **gathers** multiple elements and condenses them into a single array.<br/>
      It is mainly used in **function parameter lists** and **destructuring assignments** to *collect the remaining arguments* or elements.
      ```js
      //Function Parameter Lists
      function logAll(first, ...others) {
      console.log(first); // first argument
      console.log(others); // array of the rest
      }
      logAll(1, 2, 3, 4); // 1, [2, 3, 4]
      
      //Destructuring
      const [a, b, ...rest] = [1, 2, 3, 4, 5];
      // a = 1, b = 2, rest = [3, 4, 5]
      ```

   **[⬆ Back to Top](#table-of-contents)**

18. ### What is Loose Equality & Strict Equality Operators in Js?

      **Loose Equality**: Compares two values for equality after *performing type conversion* if necessary. This can lead to unexpected results (implicit Type Coercion), especially when comparing values of different types.
      ```js
      "5" == 5      // true (string "5" is converted to number 5)
      0 == false    // true (false is converted to 0)
      null == undefined // true
      [] == ''  //true
      [] == ![]  //true
      ```
      >Type coercion follows some ECMA Script rules for == operator. Opeartors are coerced based on operator precedence. <br/> (Paranthesis >> !,unary >> ** >> *,/,% >> +,- >> Equality >> && >> assignment). <br/>
      
      if Any Operand is: <br/>

      | Operand Type -> Converted to |   Conversion Rule    |
      |---------------------   |----------------------------|
      | Boolean -> Number      |                            |
      | Object -> Primitive    | using valueOf() toString() | 
      | String -> Number       |                            |

      If both sides are Primitives of same data type, comparison is done & coercion stops.<br/><br/>

      **Strict Equality**: Compares both value and type, without performing any type conversion. Returns true only if both operands are of the same type and have the same value. Safer & more predictable.
      ```js
      "5" === 5     // false (different types: string vs number)
      0 === false   // false (different types: number vs boolean)
      5 === 5       // true (same type and value)
      ```
   **[⬆ Back to Top](#table-of-contents)**      

19. ### What are Functions? What are ways to define them?

      A function in JavaScript is a reusable block of code designed to perform a particular task. <br/> Functions help organize and modularize code, making it easier to maintain and reuse.<br/><br/>
      a function definition needs:
      1. The **function's name** (optional for anonymous functions).
      2. Parameters (inputs the function can accept).
      3. The code to execute (inside curly braces).
      4. Optionally, a return value.
      
         1. **Function Declaration (Statement)**: Named Function with function keyword.
         Hoisted to top of its scope.   
         ```js
         //name - parameter
         function greet(name) {
         return "Hello, " + name;
         }
         greet("Deeksha"); //Deeksha - arguement
         ```    

         2. **Function Expression**: Function is assigned to a variable. can be named or anonymous.<br/> 
         Not Hoisted. Will give Reference Err due to TDZ.
         ```js
         const greet = function(name) {
         return "Hello, " + name;
         };
         ```

         3. **Arrow Function Expression (ES6)**: does not have its own `this` binding.
         ```js
         const greet = (name) => "Hello, " + name;
         ``` 

         4. **Method Definition (in Objects)**: functions are defined inside objects as methods.
         ```js
         const person = {
         greet(name) {
            return "Hello, " + name;
            }
         };
         ```

         5. **Constructor Function**: Constructor functions in JavaScript are special functions used to **create and initialize objects**. While they are defined like regular functions, their primary purpose is to serve as blueprints for new objects.<br/> Constructor functions let you easily create multiple objects with the same structure and behavior, without repeating code.

         ```js
         export const ListNode = function(val, next) {
          this.val = (val === undefined ? 0 : val)
          this.next = (next === undefined ? null : next)
         }
         //Usage: let node = new ListNode(5, null);
         ```
   | Feature  | Constructor Function  | Regular Function     |
|------------------------|-----------------------------------------------------------------|-------------------------------------------|
| Naming Convention      | Starts with an uppercase letter (e.g., `ListNode`, `Person`)    | Usually lowercase or camelCase            |
| Usage                  | Called with the `new` keyword                                   | Called directly by name                   |
| Purpose                | Creates and initializes new objects                             | Performs a task, returns a value, etc.    |
| `this` Context         | Refers to the new object being created                          | Refers to the calling context or is undefined in strict mode |
| Return Value           | Returns the new object by default                               | Returns whatever is explicitly returned   |

> creates function dynamically from a string of code. 
         ```js
         const greet = new Function("name", "return 'Hello, ' + name;");
         ```

         6. **Generator and Async Functions**: Special types of functions for advanced use cases:
            1. **Generator function**: uses function and yield.
            2. **Async function**: uses async and returns a Promise.
            ```js
            async function fetchData() {
            const response = await fetch('https://api.example.com/data');
            const data = await response.json();
            return data;
            }

            fetchData().then(data => {
            console.log(data);
            });
            ```
         **[⬆ Back to Top](#table-of-contents)**

20. ### What is a Callback Function?

      It is any function **passed as an argument** to another function, which is then **invoked** inside the outer function to complete some kind of routine or action   
      ```js
      function greet(name, callback) {
      console.log('Hello, ' + name);
      callback();
      }

      function sayGoodbye() {
      console.log('Goodbye!');
      }

      greet('Alice', sayGoodbye);
      // Output:
      // Hello, Alice
      // Goodbye!
      ```
   **[⬆ Back to Top](#table-of-contents)**

21. ### What are Higher Order Functions(HOCs)?

      **Higher-order functions** are functions that either take one or more functions as arguments, return a function as a result, or both. Array methods like array.map(), array.filter(), array.reduce() are Higher Order Functions.

      ```js
      //fn returning another fn
      function multiplier(factor) {
        return function(num) {
         return num * factor;
         };
      }
      //multiplier return a fn
      const double = multiplier(2);
      console.log(double(5)); // 10

      //fn which takes fn as an arguement
      function greet(callback) {
         console.log("Hello!");
         callback();
      }
      function sayBye() {
      console.log("Goodbye!");
      }
      greet(sayBye); // Output: Hello! Goodbye!
      ```
         **[⬆ Back to Top](#table-of-contents)**

22. ### What are Closures?

      A closure in JavaScript is a feature where an inner function has *access to the variables and parameters of its outer (enclosing) function*—even after the outer function has finished executing.
      When a function is defined inside another function, the inner function forms a closure. <br/> The closure gives the inner function access to:
      
      1. Its own scope (variables defined inside it).
      2. The scope of the outer function. 
      3. The global scope

      ```js
      function outerFunction() {
      let outerVariable = 'I am from the outer function';

      function innerFunction() {
      console.log(outerVariable);
      }

      return innerFunction;
      }

      const closureExample = outerFunction();
      closureExample(); // Output: I am from the outer function
      ```
      **[⬆ Back to Top](#table-of-contents)**

23. ### What are Objects in JS? What are ways to create it?

      Objects in JavaScript are **collections of properties**, where each *property is a key-value pair*. The value can be any type, including functions (which are then called methods). Objects are used to represent real-world entities and more complex data structures, allowing you to group related data and behavior together. <br/>

      Ways to create an Object are: <br/>
      1. **Object Literal** : 
         ```js
         const person = { firstName: "John", lastName: "Doe", age: 50, eyeColor: "blue" };
         ```
      2. **Using `new Object()` Syntax**: This creates an empty object, then properties are added.
         ```js
         const person = new Object(); // creates person = {}
         person.firstName = "John";
         person.lastName = "Doe";
         person.age = 50;
         person.eyeColor = "blue";
         ```
      3. **Constructor Functions**: This pattern is used for creating multiple similar objects.
         ```js
         function Person(first, last, age, eyeColor) {
         this.firstName = first;
         this.lastName = last;
         this.age = age;
         this.eyeColor = eyeColor;
         }
         const myFather = new Person("John", "Doe", 50, "blue");
         ```
      4. **`Object.create()`**:  This method creates a new object with the specified prototype.
         ```js
         const personPrototype = { greet() { console.log("hello!"); } };
         const carl = Object.create(personPrototype);
         ```
      5.  Others: 
            Object.assign() to copy properties from one or more objects to a new object.
            Object.fromEntries() to create objects from key-value pairs

      **[⬆ Back to Top](#table-of-contents)**         

24. ### What is Object Prototype?

      Every JavaScript object has a prototype, which is another object that it inherits properties and methods from. The prototype acts as a template object that other objects can inherit from. This is the foundation of JavaScript's **inheritance model**. <br/>
      e.g.: objects created with a *constructor function* inherit from that *constructor's prototype property*.<br/> Built-in types like Array and Date have their own prototypes (Array.prototype, Date.prototype), which in turn inherit from *Object.prototype*

      **[⬆ Back to Top](#table-of-contents)**   

25. ### What is Prototypal Inheritance?

      It is the mechanism by which objects in JavaScript *inherit properties and methods* from other objects via their *prototype chain*. When you access a property or method on an object, JavaScript will look for it on the object itself. If it's not found, it will *look up the prototype chain* until it finds it or reaches the end (Object.prototype).

         1. Objects can inherit directly from other objects.
         2. The prototype chain allows for shared behavior and code reuse.
         3. Prototypal inheritance can be implemented using Object.create(), constructor functions, or the __proto__ property.

      ```js
      const animal = { eats: true };
      const rabbit = Object.create(animal);
      console.log(rabbit.eats); // true (inherited from animal)
      ```  

      **[⬆ Back to Top](#table-of-contents)**

26.  What are Indexed Collections in React?

      These are data structures where elements are stored and accessed using numerical indexes. In JavaScript (and therefore in React), the most common indexed collection is the array, which renders list of elements. e.g. map() 
      ```js
      const items = ["Apple", "Banana", "Cherry"];
      return (
         <ul>
         {items.map((item, index) => (
            <li key={index}>{item}</li>
          ))}
         </ul>
         );
      ```  
      >Unique key is to be used for each element when rendering lists. 

      **[⬆ Back to Top](#table-of-contents)**  

27. ### What are Arrays in Js? What are its methods?

      Arrays in JavaScript are ordered collections of elements, where each element is accessed by its *numeric index (starting from 0)*. Arrays can store values of any type, including numbers, strings, objects, or even other arrays. <br/>They are widely used for managing lists and collections of data in JavaScript.
   
   | Common Array Method         | Description                                                                 |
   |----------------|   -----------------------------------------------------------------------------|
| length         | Returns the number of elements in the array                                 |
| toString()     | Converts the array to a comma-separated string                              |
| at(index)           | Returns the element at a given index                                        |
| join()         | Joins all elements into a string with a specified separator                 |
| pop()          | Removes and returns the last element                                        |
| push()         | Adds one or more elements to the end                                        |
| shift()        | Removes and returns the first element                                       |
| unshift()      | Adds one or more elements to the beginning                                  |
| concat()       | Merges arrays and/or values into a new array                                |
| slice(start,end)        | Returns a **shallow copy** of a portion of the array.<br/> start - inclusive. <br/>end - (optional, exclusive)                            |
| splice(start, deleteCount,elementsToAdd)       | Adds/removes/replaces elements at a specified index. <br/>**Mutates original Array**<br/> elementsToAdd - optional                        |
| copyWithin(target, start, end)   | Copies part of the array to another location in the same array. <br/>**Mutates original Array**. <br/> target - index where elements are to be modified from. <br/> start - index to start copying from (inclusive). <br/> end - Index to stop copying before (exclusive).            |
| flat(depth)         | Flattens nested arrays into a single array.<br/> depth - optional. <br/> Default Depth is 1.                                 |
| forEach()      | Executes a function for each array element. **returns undefined**                                  |
| map()          | Creates a new array by applying a function to each element. **returns new array**                  |
| filter()       | Creates a new array with elements that pass a test.  **Returns new array**                          |
| reduce()       | Reduces the array to a single value by executing a function on each element |
| find()         | Returns the first element that satisfies a test                             |
| findIndex()    | Returns the index of the first element that satisfies a test                |
| sort()         | Sorts the elements of the array                                             |
| reverse(callbackFn, initialVal)      | Reverses the order of the elements                                          |
| includes(value, fromIndex)     | Checks if an array contains a certain value. fromIndex - optional, index from where value must be looked from. default = 0                                  |
| indexOf(value, fromIndex)      | Returns the first index of a specified element                              |
| from()         | Creates an array from an iterable or array-like object                      |
| entries()      | Returns an iterator with key/value pairs                                    |
| keys()         | Returns an iterator with the keys (indexes)                                 |

```js
//Usage
let arr=['a','b','c'];
arr.length;                   //3

//Creating String from Array
arr.toString();               //'a,b,c'
arr.at(2);                    //"c"
arr.join('-');                //"a-b-c"

// Adding, Removing elements
arr.pop();                    //"c"
arr.push('x');                //['a','b','x']
arr.shift();                  //"a"
arr.unshift("1");             //['1','b','x']
arr.concat(['e','f','g']);    //['1','b','x','e','f','g'] 
arr.slice(-2)        //['f','g']
arr.slice()          // ['1','b','x','e','f','g']- full shallow copy
arr.splice(1,2,'a','b');   //['1','a','b','e','f','g']
arr.copyWithin(0,1,3);        // ['a','b','b','e','f','g']

//Checks array for certain Value
arr.includes('e',4)        //false
array.indexOf('b')      //1
array.indexOf('b',2)    //2

//Nested Arr
arr=[1,2,3,[4,5,[6,[7]]]];
arr.flat();                   // [1,2,3,4,5,[6,[7]]]        
arr.flat(3);                  // [1,2,3,4,5,6,7] or arr.flat(Infinite)
arr.flat(Infinity);     //flatens infinely nested array.

//Iterating & Transforming : work on callback functions
arr=[1,2,3];
arr.forEach(num => console.log(num * 2));  //  2 4 6
arr.map(num => num * 2); // [2, 4, 6]
arr.filter(num => num % 2 === 0); // [2, 4]
arr.reduce((acc, curr) => acc + curr, 0); // 6
[5, 12, 18].find(num => num > 10); // 12
[5, 12, 8].findIndex(num => num > 10);        // 1
[4, 2, 10, 1].sort((a, b) => a - b);  // [1, 2, 4, 10]
[1, 2, 3].reverse()  // [3, 2, 1]

// Creating arrays
Array.from("hello");    // ['h', 'e', 'l', 'l', 'o']

const set = new Set([1, 2, 3]);
const arr = Array.from(set);
console.log(arr); // [1, 2, 3]

const arr = ['a', 'b', 'c'];
const iterator = arr.entries();

for (const [index, value] of iterator) {
  console.log(index, value);
}
// Output:
// 0 'a'
// 1 'b'
// 2 'c'

const keys = arr.keys();

for (const key of keys) {
  console.log(key);
}
// Output:
// 0
// 1
// 2
```

**[⬆ Back to Top](#table-of-contents)**

28. ### How reduce method works?

   ```js
   let arr=[1,2,3,4];
   arr.reduce((acc, curr) => acc + curr, initialVal);    //10
   ```

   `acc`: initialVal =  0;
   reduce goes through each element, & `acc` = `acc`+`curr`
   ```js
   curr=1; acc = 0 + 1
   curr=2; acc = 1 + 2
   curr=3; acc = 3 + 3
   curr=4; acc = 6 + 4
   acc=10; //returns
   ```
   **[⬆ Back to Top](#table-of-contents)**

29. ### What are Array like Objects in Js?

   Array-like objects are objects that have *indexed elements* (properties with numeric keys) and a *non-negative length property*, similar to arrays. However, they *do not inherit* from Array.prototype and therefore *lack built-in array methods* like push(), pop(), map(), and forEach().<br/> **Features**:
   - Indexed access: Elements can be accessed using numeric indices (e.g., obj, obj[1]).
   - Length property: They have a length property indicating the number of elements.
   - No array methods: They do not have array methods such as push(), pop(), map(), or forEach().
   - Not true arrays: Array.isArray(arrayLikeObject) returns false.<br/>
   e.g.:<br/>
   - arguments object: Available inside functions, contains all arguments passed to the function.
   - DOM collections: Such as NodeList (from document.querySelectorAll) and HTMLCollection (from document.getElementsByTagName).
   - Strings: While strings are primitives, they behave like array-like objects because you can access characters by index.

   ```js
   let arrayLike = { 0: 'apple', 1: 'banana', 2: 'cherry', length: 3 };
   console.log(arrayLike[1]); // 'banana'
   console.log(arrayLike.length); // 3
   console.log(Array.isArray(arrayLike)); // false

   function showArguments() {
      console.log(arguments); // {0: ..., 1: ..., length: ...}
   }
   showArguments('a', 'b', 'c');
 
   let divs = document.querySelectorAll('div');
   console.log(divs); // NodeList {0: ..., 1: ..., length: ...}
   ```
   <br/> **Converting Array-like Objects to Arrays**:
   - Spread operator: [...arrayLikeObject]
   - Array.from(): Array.from(arrayLikeObject)
   - Object.values(): Object.values(arrayLikeObject) (for objects with numeric keys)

   **[⬆ Back to Top](#table-of-contents)** 

30. ### What are JavaScript Loops?   

   Loops in JavaScript allow you to execute a block of code multiple times, making it easier to work with collections like arrays or to repeat tasks until a condition is met.

   | Loop Type   | Description                                                                              | Common Use Case                                  |
|----------------|--------------------------------------------------------------------------------------------|--------------------------------------------------|
| `for`          | Runs code a specific number of times, with initialization, condition, and increment steps  | Iterating over arrays with known length          |
| `while`        | Runs code as long as a condition is true (condition checked before each iteration)          | When the number of iterations is not known       |
| `do...while`   | Like `while`, but always runs the code block at least once (condition checked after)        | At least one execution required                  |
| `for...in`     | Iterates over the enumerable properties of an object                                        | Looping through object keys                      |
| `for...of`     | Iterates over the values of an iterable object (like arrays, strings, etc.)                 | Looping through array or iterable values         |

## Loop Control Statements

| Statement     | Purpose                                   |
|---------------|-------------------------------------------|
| `break`       | Terminates the loop immediately           |
| `continue`    | Skips to the next iteration of the loop   |
| Labeled loops | Control flow in nested loops 

   **[⬆ Back to Top](#table-of-contents)** 

31. ### What is Lexical Scoping in Js?

   Lexical scoping (also called static scoping) is a fundamental concept in JavaScript that determines how variable names are resolved in nested functions. In lexical scoping, the scope of a variable is determined by its position within the source code—specifically, where it is declared—not by where or how functions are called.

   **How it works?**
   -When a function is defined inside another function, the inner function has access to variables declared in its own scope as well as in all of its outer (parent) scopes, up to the global scope.-This relationship is established at the time of function declaration, not at the time of function invocation.

   ```js
   function outerFunction() {
     let outerVariable = 'I am outside!';
     function innerFunction() {
      outerVar
       console.log(outerVariable); // 'I am outside!'
     }
     innerFunction();
   }
   outerFunction();
   ```

   **Scope Chain**:
   When JavaScript looks up a variable, it starts in the current scope. If the variable isn't found, it moves up to the parent scope, and continues this process until it reaches the global scope or finds the variable.

   > JavaScript uses lexical scope, so functions always have access to variables where they were defined, not where they are called.

   **Lexical Scoping and Closures**
   Closures are functions that "remember" their lexical scope, even after the outer function has finished executing. This allows inner functions to retain access to variables from their parent scopes.
   ```js
   function counter() {
     let count = 0;
      return function() {
      count++;
      console.log(count);
     }
   }
   const increment = counter();
   increment(); // 1
   increment(); // 2
   ```

   **Tricky Question**:
   ```js
   let funcs = [];
   for (var i = 0; i < 3; i++) {
     funcs.push(function() {
       console.log(i);
     });
   }
   funcs[0]();
   funcs[1]();
   funcs[2]();
   //Output: 
   //3
   //3
   //3
   //if i -> let , output => 0 1 2

   let funcs = [];

   for (var i = 0; i < 3; i++) {
     (function(j) {
       funcs.push(function() {
         console.log(j);
       });
     })(i);
   }

   funcs[0](); // 0
   funcs[1](); // 1
   funcs[2](); // 2
   ```




