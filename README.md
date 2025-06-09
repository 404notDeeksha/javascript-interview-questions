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
| 6   | [What is Client side Rendering & Server side Rendering?](#what-is-client-side-rendering--server-side-rendering)                                                  |
| 6   | [What is Client side & Server side? ](#what-is-client-side--server-side)                                                  |
| 6   | [What is Client side & Server side? ](#what-is-client-side--server-side)                                                  |
| 6   | [What is Client side & Server side? ](#what-is-client-side--server-side)                                                  |
| 6   | [What is Client side & Server side? ](#what-is-client-side--server-side)                                                  |
| 6   | [What is Client side & Server side? ](#what-is-client-side--server-side)                                                  |

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

   In *Client Side Rendering*, *browser* is responsible for rendering the web page. The server sends a basic HTML File & a Js bundle (after site has been deployed on a server). Browser runs the Js bundle which generates & displays UI. After Initial load, all updates & navigation happen in browser using Js. without reloading entire page. <br/><ul><li> It reduces Server load, as server mainly handles API/ data requests & not page rendering. <br/><li> It leads to Interactive , dynamic user Experience, smoother navigation & real time updates.<li> <br/> It also means slower initial load times, because browser needs to download & exceute Js before showing content.</ul>

7. ### What is scope in Js?



