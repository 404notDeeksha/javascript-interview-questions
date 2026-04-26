# JavaScript Code Processing Stages

Stages are:

1. **Parsing**: Js engine first parses the code (it reads Js source code, & checks for syntax errors. It converts code into structured format (DSA) called Abstract Syntax Tree (AST)). Parsing ensures code is valid for further processing.

2. **Compilation/Interpretation**: modern Js engines use mix of JIT (Just-in-time) compilation & interpretation. Engine converts parsed code into machine code/ bytecode which computer can execute. This step involves optimisation for faster execution.

3. **Execution Context Creation**: Before running the code, the engine creates an execution context. This is an environment where the code will run, including memory for variables and functions. It is of 2 main types:

   - **Global Execution Context** (for code outside functions) only 1 exists.
     It has 2 phases:
     - (1) Memory Creation Phase (Hoisting phase)
       Variables → initialized as undefined
       Functions → stored entirely in memory
     - (2) Code Execution Phase
       Code runs line by line
       Variables get actual values

   ```js
   var a = 10;

   function foo() {
     console.log("Hello");
   }
   console.log(a);

   // Memory Phase:
   // a: undefined
   // foo: function definition

   // Execution Phase:
   a = 10
   foo → ready
   console.log(a) → 10
   ```

   - **Function Execution Context** (created each time a function is called, gets its own memory & own scope).

   ```js
   function greet(name) {
     var msg = "Hello " + name;
     return msg;
   }

   greet("Deeksha");

   // 1. GEC created
   // 2. greet() is called → new FEC created
   // 3. Inside FEC:
   ```

4. **Memory Allocation (Creation Phase)**: In each execution context, the engine performs a memory allocation phase (also called the "creation phase"). It sets up the variable environment, allocating space for variables and functions, and hoisting declarations as needed.

5. **Code Execution (Execution Phase)**: The engine then executes the code line by line. It assigns values to variables, evaluates expressions, and runs function calls.

6. **Call Stack (Execution Context Stack)**: As functions are called, execution contexts are pushed onto the call stack (since Js is single threaded language). When a function finishes, its context is popped off the stack.

   ```js
   function one() {
     two();
   }

   function two() {
     three();
   }

   function three() {
     console.log("Done");
   }

   one();

   // Call Stack Flow: Global → one → two → three
   // Unwind Flow: three → two → one → Global
   ```

7. **Handling Asynchronous Code (Event Loop)**: For asynchronous operations (like setTimeout, Promises, AJAX), the engine interacts with the browser's Web APIs, callback queue, and microtask queue. The event loop ensures that asynchronous callbacks are executed when the call stack is empty.
