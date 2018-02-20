# Events

* In node if you require the events module you can use the so-called **'event emitter'**.

* Events are a common pattern in programming, known more widely as the 'observer pattern' or 'pub/sub' (publish/subscribe).

* Whereas callbacks are a one-to-one relationship, events are the same exact pattern except with a many-to-many API.

* You can say <strong>'when X do Y'</strong>, whereas with plain callbacks it is <strong>'do X then Y'</strong>.

Here are few common use cases for using events instead of plain callbacks:

* Chat room where you want to broadcast messages to many listeners

* Game server that needs to know when new players connect, disconnect, move, shoot and jump

* Game engine where you want to let game developers subscribe to events like `.on('jump', function() {})`

* A low level web server that wants to expose an API to easily hook into events that happen like `.on('incomingRequest')` or `.on('serverError')`

If we were trying to write a module that connects to a chat server using only callbacks it would look like this:

```javascript
var chatClient = require('my-chat-client')

function onConnect() {
  // have the UI show we are connected
}

function onConnectionError(error) {
  // show error to the user
}

function onDisconnect() {
 // tell user that they have been disconnected
}

function onMessage(message) {
 // show the chat room message in the UI
}

chatClient.connect(
  'http://mychatserver.com',
  onConnect,
  onConnectionError,
  onDisconnect,
  onMessage
)
```

Writing this with events would look like this:

```javascript
var chatClient = require('my-chat-client').connect()

chatClient.on('connect', function() {
  // have the UI show we are connected
})

chatClient.on('connectionError', function() {
  // show error to the user
})

chatClient.on('disconnect', function() {
  // tell user that they have been disconnected
})

chatClient.on('message', function() {
  // show the chat room message in the UI
})
```

## Exercises

What will be print to the console?

```javascript
const myEmitter = new MyEmitter();
let m = 0;
myEmitter.on('event', () => {
  m += 1
  console.log(m);
});
myEmitter.emit('event');
myEmitter.emit('event');
myEmitter.emit('event');
```
