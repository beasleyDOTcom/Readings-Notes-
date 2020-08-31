# TCP servers and event driven programming

## Given the examples of front-end events such as button click, window resize, form submit, etc, what are some examples of back-end events? 
When a route is hit that triggers a callback function. 
## Why are events sometimes better than asynchronous actions with callbacks?
because it came make for a more responseive GUI:

Generally speaking, a 'callback' is under the control of the detecting process. So you tell a GUI manager "call myaction when this button is pressed" and the GUI manager calls the action when the button is pressed.

Event Handlers on the other hand operate at one step removed. The GUI manager is configured to send messages to an event handler. You tell an event manager that button pushes are handled by the myaction program. When the button is pushed the GUI manager puts a message on the event handler's queue and gets on with GUI managing. The event handler picks up the message from the queue, sees it's a button push, fires up the myaction program, and moves on to handling the next event. Usually the myaction program will run as an independent thread or even a separate process.

While the "event handler" pattern is more complex it is much more robust and less likely to hang when an action fails. It also makes for a more responsive GUI.
resource: https://stackoverflow.com/questions/2069763/difference-between-event-handlers-and-callbacks#:~:text=Usually%20the%20myaction%20program%20will,for%20a%20more%20responsive%20GUI.&text=A%20callback%20is%20procedure%20you%20pass%20as%20an%20argument%20to%20another%20procedure.
## What does an EventEmitter instance do?
All objects that emit events are instances of the EventEmitter class. These objects expose an eventEmitter.on() function that allows one or more functions to be attached to named events emitted by the object. Typically, event names are camel-cased strings but any valid JavaScript property key can be used.

When the EventEmitter object emits an event, all of the functions attached to that specific event are called synchronously. Any values returned by the called listeners are ignored and will be discarded.

The following example shows a simple EventEmitter instance with a single listener. The eventEmitter.on() method is used to register listeners, while the eventEmitter.emit() method is used to trigger the event.
resource: https://nodejs.org/api/events.html#:~:text=All%20objects%20that%20emit%20events,events%20emitted%20by%20the%20object.&text=The%20following%20example%20shows%20a%20simple%20EventEmitter%20instance%20with%20a%20single%20listener.
## When is a program’s call stack, event queue, and event loop active?
the call stack is where code gets pushed to and then read line by line as the interpreter reads the program.
the event queue is where your asynchronous code gets pushed to, and waits for the execution.
The Event Loop, which keeps running continuously and checks the Main stack, if it has any frames to execute, if not then it checks Callback queue, if Callback queue has codes to execute then it pops the message from it to the Main Stack for the execution.
to answer, I think the call stack is waiting for stuff to run, the event queue is chilling on the side waiting to be invoked, and the event loop is always listening for someone to ask it for something.
resource: https://medium.com/@Rahulx1/understanding-event-loop-call-stack-event-job-queue-in-javascript-63dcd2c71ecd#:~:text=Event%20Loop%3A%20Then%20comes%20the,Main%20Stack%20for%20the%20execution.
# Document the following Vocabulary Terms
## Observer Pattern
The observer pattern is a software design pattern in which an object, called the subject, maintains a list of its dependents, called observers, and notifies them automatically of any state changes, usually by calling one of their methods. 
resource: https://en.wikipedia.org/wiki/Observer_pattern
## Listener
an event listener is a function that is running waiting for a specified event to occur so that it can trigger a event.
## Event Handler
an event handler is what gets told to perform whenever the listener was triggered, usually a function.

## Event Driven Programming
In computer programming, event-driven programming is a programming paradigm in which the flow of the program is determined by events such as user actions (mouse clicks, key presses), sensor outputs, or messages from other programs or threads.
resource: https://en.wikipedia.org/wiki/Event-driven_programming#:~:text=In%20computer%20programming%2C%20event%2Ddriven,from%20other%20programs%20or%20threads.
## Event Loop
the event loop is a programming construct or design pattern that waits for and dispatches events or messages in a program. The event loop works by making a request to some internal or external "event provider", then calls the relevant event handler.
resource: https://en.wikipedia.org/wiki/Event_loop
## Event Queue
Search Results
Featured snippet from the web
A queue that contain events inside. Events occur in an asynchronous manner at the OperatingSystem level. The OperatingSystem may respond to events immediately or put them in an EventQueue for later processing.
resource: https://wiki.c2.com/?EventQueue#:~:text=A%20queue%20that%20contain%20events,an%20EventQueue%20for%20later%20processing.
## Call Stack
call stack is where asynchronus code goes to be run in a last in first out kind a way.
## Emit/Raise/Trigger
Much of the Node.js core API is built around an idiomatic asynchronous event-driven architecture in which certain kinds of objects (called "emitters") emit named events that cause Function objects ("listeners") to be called.

For instance: a net.Server object emits an event each time a peer connects to it; a fs.ReadStream emits an event when the file is opened; a stream emits an event whenever data is available to be read.

All objects that emit events are instances of the EventEmitter class. These objects expose an eventEmitter.on() function that allows one or more functions to be attached to named events emitted by the object. Typically, event names are camel-cased strings but any valid JavaScript property key can be used.

When the EventEmitter object emits an event, all of the functions attached to that specific event are called synchronously. Any values returned by the called listeners are ignored and will be discarded.
resource: https://nodejs.org/api/events.html
## Subscribe
I think this is hwo you get realtime notificatinos of somethings.
## database

a place where data can be stored. 
