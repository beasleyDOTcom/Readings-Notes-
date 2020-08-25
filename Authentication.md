# authentication

 - [x] Explain what a “Singleton” is (in Computer Science terms)
 In software engineering, the singleton pattern is a software design pattern that restricts the instantiation of a class to one "single" instance. This is useful when exactly one object is needed to coordinate actions across the system. The term comes from the mathematical concept of a singleton.
 reference: https://en.wikipedia.org/wiki/Singleton_pattern

Critics consider the singleton to be an anti-pattern in that it is frequently used in scenarios where it is not beneficial, introduces unnecessary restrictions in situations where a sole instance of a class is not actually required, and introduces global state into an application.[1][2][3][4]
 - [x] Explain how the Singleton pattern can be used with Node modules, specifically with classes
 The Singleton Problem
 The singleton[5] design pattern is one of the twenty-three well-known "Gang of Four" design patterns that describe how to solve recurring design problems to design flexible and reusable object-oriented software, that is, objects that are easier to implement, change, test, and reuse.

The singleton design pattern solves problems like:[6]

How can it be ensured that a class has only one instance?
How can the sole instance of a class be accessed easily?
How can a class control its instantiation?
How can the number of instances of a class be restricted?
How can a global variable be accessed?
The singleton design pattern describes how to solve such problems:

Hide the constructor of the class.
Define a public static operation (getInstance()) that returns the sole instance of the class.
The key idea in this pattern is to make the class itself responsible for controlling its instantiation (that it is instantiated only once).
The hidden constructor (declared private) ensures that the class can never be instantiated from outside the class.
The public static operation can be accessed easily by using the class name and operation name (Singleton.getInstance()).
resource: https://en.wikipedia.org/wiki/Singleton_pattern
 ========================================================================================
Sometimes you need to make sure that you have one and only one instance of an object. This is where the singleton pattern can be useful. A singleton represents a single instance of an object. Only one can be created, no matter how many times the object is instantiated. If there’s already an instance, the singleton will create a new one. Let’s take a look at where creating multiple instances of one object might create problems within our application.
Lets create some files in node.js. First file is Logger.js.

Within this file, we create a class called Logger. The idea is that we want our application modules to use this logger class instead of using console log directly. This logger saves information about all of the logs that are sent to it and it also logs each message with a timestamp. So once we create an instance of this object we can use the log method, send it a message, and it will log the timestamp and the message to the terminal as well as save information about that log.
Created another file named as Store.js

Now if you look at this file we actually use the Logger. On line one, we import the Logger class, and on line three we create a new instance called Logger so that we can actually use this class. So on line 10, within the store constructor we will log a new message every time a store is created. So it says New Store and it gives us the name of the store and how many items are in stock.
The third file we have is Shopper.js

If you take a look at the shopper.js file it also uses the Logger, and on line 3 it creates its own instance of the Logger. So, whenever we create new shoppers on line 10 within the constructor, we will log a message to the console that says a new shopper has been created,this is their name and this is how much money they have in their account.
Finally, the index_singleton.js, the main entry point for our application.

Within our index_singleton.js, we are also using the Logger. On line one we import the class, and on line five we create our third instance of the Logger. Now, this file also uses the store and shopper classes and on line nine we create a new instance of a shopper and on line 11 we’ll create a new instance of a store.Now notice on line seven, we are sending messages to the Logger. So, on line seven we’re going to log the message starting app and on line 24 we’re also going to log the message finished config.
Now down here on line 25 of this file we’re using console log just to dump some debugging information. So here we’ll see how many messages have been saved inside of our Logger instance and on line 27 we’ll actually log each of those messages by mapping the logs array.So, the Logger instance stores an array called logs. We’re going to map over each item in that array, and we’re going to log the message that’s saved there to the console. Let’s go ahead and go out to our console and run this application.
node index_singleton.js
2018-04-30T14:43:58.748Z - Strarting app....
2018-04-30T14:43:58.897Z - Shopper: alex has 500 money in their account
2018-04-30T14:43:58.900Z - New Store: Jai Vinayak Collection has 2 items in stock
2018-04-30T14:43:58.901Z - finsihed config....
Total log count: 2
Strarting app....
finsihed config....
we will notice that we see four logs. So we see our main application, log, starting the app along with its timestamp. We see that a new shopper has been created, a new store has been created, and then our main application has also finished running the configuration. The problem is, is because we have three instances of the Logger, we’re only looking at the information for the main instance. So in our debugging information down here we see two logs total and those logs are only starting app and finished config. Now the reason is, is whenever we looking at the current Logger instance, we’re only looking at the instance that was created within our main application.
Not the instance that was created within the shopper and the store. When we have this type of a problem a singleton can really come in handy.
How to create Singleton Instance in Node.js?
In the last Section we took a look at how creating multiple instances of the logger class can cause problems within our application. In this section we’re going to go ahead and fix those problems by implementing a singleton. So logger.js file let’s go ahead and modify this file to export a singleton instead of a logger. So on line 17 I’m just going to come in here and add a new class called singleton. So this class is only going to allow us to create one instance of the logger. Anytime we need that instance we’re going to retrieve it through a get instance method.
So let’s go ahead and add a constructor to our singleton class. And what we want to do within this constructor is we want to check and see if an instance has already been created. So I’m going to save the instance directly to the class. So if there’s not a singleton instance then we want to create one. So if we don’t have one then the singleton instance will equal new logger. So that’s our singleton. And it will only allow us to create one instance whenever we instantiate this singleton class.
So the next thing we’re going to do for a classical singleton is actually return that instance using a get instance method. And what we can do within this method is return our singleton instance. There we go. So this class only allows us to instantiate one logger and then using the get instance method we can return that logger to any file that wants to use it.

So let’s go ahead and go into our store. We need to modify line three, where we create a new instance of our logger class to have a .getInstance chained on that call.

So this will return our single instance. And then within the shopper js we need to do the same thing also on line three .getInstance.

And now both the store and the shopper should be using the same single instance of the logger. Within the index.js file we’ll also chain on a .getInstance and now all three of these files should be using the exact same instance of the logger.

So we can check this by going to run our application. So let’s go out to the terminal and node index.js. And now we see the same output. We see four logs starting the app coming from our index file.
New shopper coming from the shopper file. New store coming from the store file. And then finished config coming from the index. And we also see the correct amount of logs within our logger instance. So it says that we have four logs total and it shows us that all four of these logs have made it even though we’re using the logger throughout multiple files.
2018-04-30T15:50:22.942Z - starting app...
2018-04-30T15:50:22.966Z - New Shopper: alex has 500 in their account.
2018-04-30T15:50:22.967Z - New Store: Steep and Deep Supplies has 2 items in stock.
2018-04-30T15:50:22.967Z - finished config...
4 logs total
   starting app...
   New Shopper: alex has 500 in their account.
   New Store: Steep and Deep Supplies has 2 items in stock.
   finished config...
Can we fix Singleton probelm without creating a new Singleton class. Answer is yes.
I’m going to come into my logger.js file and just implement the singleton an easier way by removing the class. Or the need to export a single class and now on line 19 where I export this module, I’m going to just go ahead and export a new instance of the logger. The idea here is that when we run this file, it will run once, create the new instance of the logger, and save it in the cache. That means that Node JS will automatically handle exporting the same instance of the logger to every other module that wants to consume it.

So, let’s just go ahead and modify our store.js file and Shopper.js. We are going to get rid of line three where we create the instance of the logger here because we’re going to import it directly from our logger module.
So, we are importing the instance and then I am getting rid of the line where we created the new logger instance. So, I go ahead and save this and we should have the exact same results without the need to create an extra class. So, let’s go ahead and test this out.
resource: https://medium.com/@maheshkumawat_83392/node-js-design-patterns-singleton-pattern-series-1-1e0ab71e3edf
 - [x] If you were tasked with building a middleware system like Express uses, what approach might you take to construct/operate it?

# Document the following Vocabulary Terms
## Term
### Router Middleware
Middleware functions are functions that have access to the request object (req), the response object (res), and the next middleware function in the application’s request-response cycle. The next middleware function is commonly denoted by a variable named next.

Middleware functions can perform the following tasks:

Execute any code.
Make changes to the request and the response objects.
End the request-response cycle.
Call the next middleware function in the stack.
If the current middleware function does not end the request-response cycle, it must call next() to pass control to the next middleware function. Otherwise, the request will be left hanging.

An Express application can use the following types of middleware:

Application-level middleware
Router-level middleware
Error-handling middleware
Built-in middleware
Third-party middleware
You can load application-level and router-level middleware with an optional mount path. You can also load a series of middleware functions together, which creates a sub-stack of the middleware system at a mount point.
THIS RESOURCE IS ACTUALLY HELPFUL
RESOURCE: https://expressjs.com/en/guide/using-middleware.html
### Dynamic Module Loading
This proposal was made by Domenic Denicola and it enables dynamic loading of ECMAScript modules. Currently ECMAScript modules are static: you must specify what you want to import and export at compile time and this static structure of imports is enforced syntactically in two ways. Let’s see an example:
import * as myModule from './myModule.js';
This import declaration can only appear at the top level of a module, which prevents you from importing modules inside any other statements and also the module specifier './myModule.js' cannot be computed at runtime.
With import() operator we can load modules dynamically. Let’s see some examples:
const myModule = './myModule.js';
import(myModule)
   .then(x => x.someMethod());
The operator is used like a function and the parameter is a string with a module specifier (path of the module). In contrast to the current “import”, the parameter can be any expression whose result can be coerced to a string and the result of the “function call” is a Promise. Once the module is loaded, the Promise is fulfilled with it and you are good to go.
The import() works like a function, but it is an operator: In order to resolve “module specifiers” relatively to the current module, it needs to know from which module it is invoked.
Ok, once this feature was released, we can do many interesting things, for example: some web app feature doesn’t have to be present when app starts and it can be loaded on demand. Let’s see an example:
btnUpdate.addEventListener('click', event => {
    import('./myModule.js')
    .then(x => {
        x.someInterestedFunction();
    })
    .catch(error => {
        /* Error handling */
    })
});
We can load some modules depending on whether a condition is true. For example:
if (someCondition()) {
   import('./myModule.js')
      .then(x => x.someMethod());
}
You can compute module specifiers like this:
import(`messages_${getCurrentLanguage()}.js`)
   .then(...);
There are another details I could talk about, but I will wait for the stage 4 in
### Singleton Pattern
The singleton design pattern solves problems like:[6]

How can it be ensured that a class has only one instance?
How can the sole instance of a class be accessed easily?
How can a class control its instantiation?
How can the number of instances of a class be restricted?
How can a global variable be accessed?
The singleton design pattern describes how to solve such problems:

Hide the constructor of the class.
Define a public static operation (getInstance()) that returns the sole instance of the class.
The key idea in this pattern is to make the class itself responsible for controlling its instantiation (that it is instantiated only once).
The hidden constructor (declared private) ensures that the class can never be instantiated from outside the class.
The public static operation can be accessed easily by using the class name and operation name (Singleton.getInstance()).
resource: https://en.wikipedia.org/wiki/Singleton_pattern
### CRUD -> REST Method Matches
create POST
READ Get
Update PUT/Patch
Delete Destroy
### Mock Testing
Mock testing is an approach to unit testing that lets you make assertions about how the code under test is interacting with other system modules. In mock testing, the dependencies are replaced with objects that simulate the behaviour of the real ones. The purpose of mocking is to isolate and focus on the code being tested and not on the behaviour or state of external dependencies.
resource: https://devopedia.org/mock-testing#:~:text=Mock%20testing%20is%20an%20approach,behaviour%20of%20the%20real%20ones