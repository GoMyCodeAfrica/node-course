# Callbacks

* Nearly everything in node uses callbacks.

* Callbacks are functions that are executed asynchronously, or at a later time.

* Here is a simple <strong>synchronous</strong> example:

```javascript
let number = 1
function addOne(num) {
	return num + 1
}

let result = addOne(number)
console.log(result) // logs out 2
```

Node, uses mostly <strong>asynchronous</strong> code.

Let's use node to read our number from a file called `number.txt`

```javascript
const fs = require('fs')   // require is a special function provided by node
let number // we don't know what the number is yet since it is stored in a file

function addOne() {
  fs.readFile('number.txt', function readNumber(err, fileContents) {
    number = Number(fileContents)
    number += 1
  })
}

addOne()

console.log(number) // logs out undefined -- this line gets run before readFile is done
```

* In this code we use the `fs.readFile` method, which is asynchronous.

* Usually things that have to talk to hard drives or networks will be <strong>asynchronous</strong>.

* If they just have to access things in memory or do some work on the CPU they will be <strong>synchronous</strong>.

* The reason for this is that I/O is very sloow.

Let's put our `console.log` statement into a function and pass it in as a callback:

```javascript
const fs = require('fs')
let number

function addOne(callback) {
  fs.readFile('number.txt', function readNumber(err, fileContents) {
    number = Number(fileContents)
    number += 1
    callback()
  })
}

function logNumber() {
  console.log(number)
}

addOne(logNumber)
```

Now the `logNumber` function can get passed in as an argument that will become the callback variable inside the `addOne` function.

After `readFile` is done the `callback` variable will be invoked (`callback()`).


1. The code is parsed, which means if there are any syntax errors they would make the program break. During this initial phase, `fs` and `number` are declared as variables while `addOne` and `logNumber` are declared as functions.

2. When the last line of our program gets executed addOne is invoked with the `logNumber` function passed as its callback argument. Invoking `addOne` will first run the asynchronous `fs.readFile` function.

3. With nothing to do, node idles for a bit as it waits for `readFile` to finish.

3. As soon as readFile finishes it executes its callback, `readNumber`, which parses `fileContents` for an integer called `number`, increments `number` and then immediately invokes the function that `addOne`  passed in (its callback), `logNumber`.

## Exercises

Write an asynchronous function **getUser** that given a user identifier and a callback function.

If the user identifier is an integer then a fake user should be passed to the callback, otherwise pass an error to the callback where it's handled.
