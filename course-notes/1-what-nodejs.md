# What's Node.js

* Node.js is a C++ program.

* Node.js uses V8 (JavaScript engine inside chrome) to exectue JavaScript programs.

* Node.js is a JavaScript runtime.

* Node.js offers a collection of JavaScript functions (APIs) that facilitate I/O operations such as:
  - Read/Write (I/O) from files.
  - Read/Write (I/O) from remote servers (APIs).
  - Read/Write (I/O) from databases.

* Node.js makes JavaScript more like Java, Python etc.

* Node.js is a good choice for heavy I/O applications (web servers).

# V8

<p align="center">
  <img src="./assets/images/v8logo.png">
</p>

* **V8** is Google’s open source JavaScript engine.

* **V8** exectues JavaScript programs very very fast (high-performance engine)

# Differences between Node and browser environment.

1. Node and Chrome both uses V8 as a JavaScript engine.

2. **window** is the global variable for browsers.

3. **global** is the global variable in Node.

4. **document** represents the DOM tree for browsers.

5. **process** represents the process running the JavaScript program.

## Summary

Node.js is

* A JavaScript runtime.

* Uses V8 as JavaScript engine

* offers some functions/objects to:
  - Read/Write from files.
  - Read/Write from databases.
  - Read/Write from remote servers.


## Exercises

**Paying with Node REPL**

1. Open your **terminal** and type **node -v** to make sure that you have node installed.

2. Write a JavaScript function and call it inside the repl.

3. Try to use some JavaScript values from the browser environment and see if they still work:
  - setTimeout, setInterval
  - console.log, console.warn
  - alert, prompt, confirm

4. Try to inspect some node global valirable such as
  - **process**
  - **process.pid**
  - **process.argv**
  - **process.env**
  - **process.env.Path**
