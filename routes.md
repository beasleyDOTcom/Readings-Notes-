# Summary of contents
This reading is all about route handling. 
Routes can be managed in separate modules from the main server, allowing us to extract that logic and wiring to be more topical.


index.js - Entry Point
server.js - Hub, Exported Server
models/categories.js, etc - Data Models
routes/categories.js, etc - Routers and Handlers



# Routing

Routing refers to how an application’s endpoints (URIs) respond to client requests. For an introduction to routing, see Basic routing.

You define routing using methods of the Express app object that correspond to HTTP methods; for example, app.get() to handle GET requests and app.post to handle POST requests. For a full list, see app.METHOD. You can also use app.all() to handle all HTTP methods and app.use() to specify middleware as the callback function (See Using middleware for details).

These routing methods specify a callback function (sometimes called “handler functions”) called when the application receives a request to the specified route (endpoint) and HTTP method. In other words, the application “listens” for requests that match the specified route(s) and method(s), and when it detects a match, it calls the specified callback function.

In fact, the routing methods can have more than one callback function as arguments. With multiple callback functions, it is important to provide next as an argument to the callback function and then call next() within the body of the function to hand off control to the next callback.

## The following code is an example of a very basic route.

var express = require('express')
var app = express()

// respond with "hello world" when a GET request is made to the homepage
app.get('/', function (req, res) {
  res.send('hello world')
})
Route methods
A route method is derived from one of the HTTP methods, and is attached to an instance of the express class.

The following code is an example of routes that are defined for the GET and the POST methods to the root of the app.

// GET method route
app.get('/', function (req, res) {
  res.send('GET request to the homepage')
})

// POST method route
app.post('/', function (req, res) {
  res.send('POST request to the homepage')
})
## Express supports methods that correspond to all HTTP request methods: get, post, and so on. For a full list, see app.METHOD.

There is a special routing method, app.all(), used to load middleware functions at a path for all HTTP request methods. For example, the following handler is executed for requests to the route “/secret” whether using GET, POST, PUT, DELETE, or any other HTTP request method supported in the http module.

app.all('/secret', function (req, res, next) {
  console.log('Accessing the secret section ...')
  next() // pass control to the next handler
})
## Route paths
Route paths, in combination with a request method, define the endpoints at which requests can be made. Route paths can be strings, string patterns, or regular expressions.

The characters ?, +, *, and () are subsets of their regular expression counterparts. The hyphen (-) and the dot (.) are interpreted literally by string-based paths.

If you need to use the dollar character ($) in a path string, enclose it escaped within ([ and ]). For example, the path string for requests at “/data/$book”, would be “/data/([\$])book”.

Express uses path-to-regexp for matching the route paths; see the path-to-regexp documentation for all the possibilities in defining route paths. Express Route Tester is a handy tool for testing basic Express routes, although it does not support pattern matching.

Query strings are not part of the route path.

Here are some examples of route paths based on strings.

This route path will match requests to the root route, /.

app.get('/', function (req, res) {
  res.send('root')
})
This route path will match requests to /about.

app.get('/about', function (req, res) {
  res.send('about')
})
This route path will match requests to /random.text.

app.get('/random.text', function (req, res) {
  res.send('random.text')
})
## Here are some examples of route paths based on string patterns.

This route path will match acd and abcd.

app.get('/ab?cd', function (req, res) {
  res.send('ab?cd')
})
This route path will match abcd, abbcd, abbbcd, and so on.

app.get('/ab+cd', function (req, res) {
  res.send('ab+cd')
})
This route path will match abcd, abxcd, abRANDOMcd, ab123cd, and so on.

app.get('/ab*cd', function (req, res) {
  res.send('ab*cd')
})
This route path will match /abe and /abcde.

app.get('/ab(cd)?e', function (req, res) {
  res.send('ab(cd)?e')
})
## Examples of route paths based on regular expressions:

This route path will match anything with an “a” in it.

app.get(/a/, function (req, res) {
  res.send('/a/')
})
This route path will match butterfly and dragonfly, but not butterflyman, dragonflyman, and so on.

app.get(/.*fly$/, function (req, res) {
  res.send('/.*fly$/')
})
# Route parameters
Route parameters are named URL segments that are used to capture the values specified at their position in the URL. The captured values are populated in the req.params object, with the name of the route parameter specified in the path as their respective keys.

Route path: /users/:userId/books/:bookId
Request URL: http://localhost:3000/users/34/books/8989
req.params: { "userId": "34", "bookId": "8989" }
To define routes with route parameters, simply specify the route parameters in the path of the route as shown below.

app.get('/users/:userId/books/:bookId', function (req, res) {
  res.send(req.params)
})
The name of route parameters must be made up of “word characters” ([A-Za-z0-9_]).

Since the hyphen (-) and the dot (.) are interpreted literally, they can be used along with route parameters for useful purposes.

Route path: /flights/:from-:to
Request URL: http://localhost:3000/flights/LAX-SFO
req.params: { "from": "LAX", "to": "SFO" }
Route path: /plantae/:genus.:species
Request URL: http://localhost:3000/plantae/Prunus.persica
req.params: { "genus": "Prunus", "species": "persica" }
To have more control over the exact string that can be matched by a route parameter, you can append a regular expression in parentheses (()):

Route path: /user/:userId(\d+)
Request URL: http://localhost:3000/user/42
req.params: {"userId": "42"}
Because the regular expression is usually part of a literal string, be sure to escape any \ characters with an additional backslash, for example \\d+.

### In Express 4.x, the * character in regular expressions is not interpreted in the usual way. As a workaround, use {0,} instead of *. This will likely be fixed in Express 5.

# Route handlers
You can provide multiple callback functions that behave like middleware to handle a request. The only exception is that these callbacks might invoke next('route') to bypass the remaining route callbacks. You can use this mechanism to impose pre-conditions on a route, then pass control to subsequent routes if there’s no reason to proceed with the current route.

Route handlers can be in the form of a function, an array of functions, or combinations of both, as shown in the following examples.

A single callback function can handle a route. For example:

app.get('/example/a', function (req, res) {
  res.send('Hello from A!')
})
More than one callback function can handle a route (make sure you specify the next object). For example:

app.get('/example/b', function (req, res, next) {
  console.log('the response will be sent by the next function ...')
  next()
}, function (req, res) {
  res.send('Hello from B!')
})
An array of callback functions can handle a route. For example:

var cb0 = function (req, res, next) {
  console.log('CB0')
  next()
}

var cb1 = function (req, res, next) {
  console.log('CB1')
  next()
}

var cb2 = function (req, res) {
  res.send('Hello from C!')
}

app.get('/example/c', [cb0, cb1, cb2])
## A combination of independent functions and arrays of functions can handle a route. For example:

var cb0 = function (req, res, next) {
  console.log('CB0')
  next()
}

var cb1 = function (req, res, next) {
  console.log('CB1')
  next()
}

app.get('/example/d', [cb0, cb1], function (req, res, next) {
  console.log('the response will be sent by the next function ...')
  next()
}, function (req, res) {
  res.send('Hello from D!')
})
### Response methods
#### The methods on the response object (res) in the following table can send a response to the client, and terminate the request-response cycle. If none of these methods are called from a route handler, the client request will be left hanging.

# Method	Description
res.download()	Prompt a file to be downloaded.
res.end()	End the response process.
res.json()	Send a JSON response.
res.jsonp()	Send a JSON response with JSONP support.
res.redirect()	Redirect a request.
res.render()	Render a view template.
res.send()	Send a response of various types.
res.sendFile()	Send a file as an octet stream.
res.sendStatus()	Set the response status code and send its string representation as the response body.
app.route()
You can create chainable route handlers for a route path by using app.route(). Because the path is specified at a single location, creating modular routes is helpful, as is reducing redundancy and typos. For more information about routes, see: Router() documentation.

## Here is an example of chained route handlers that are defined by using app.route().

app.route('/book')
  .get(function (req, res) {
    res.send('Get a random book')
  })
  .post(function (req, res) {
    res.send('Add a book')
  })
  .put(function (req, res) {
    res.send('Update the book')
  })
express.Router
Use the express.Router class to create modular, mountable route handlers. A Router instance is a complete middleware and routing system; for this reason, it is often referred to as a “mini-app”.

The following example creates a router as a module, loads a middleware function in it, defines some routes, and mounts the router module on a path in the main app.

Create a router file named birds.js in the app directory, with the following content:

var express = require('express')
var router = express.Router()

// middleware that is specific to this router
router.use(function timeLog (req, res, next) {
  console.log('Time: ', Date.now())
  next()
})
// define the home page route
router.get('/', function (req, res) {
  res.send('Birds home page')
})
// define the about route
router.get('/about', function (req, res) {
  res.send('About birds')
})

module.exports = router
Then, load the router module in the app:

var birds = require('./birds')

// ...

app.use('/birds', birds)
The app will now be able to handle requests to /birds and /birds/about, as well as call the timeLog middleware function that is specific to the route.

# --------------------------------------------------------------------------------------------------

With the new ExpressJS 4.0 just being released last week, there are many changes that have come with it. These changes will affect how we build Node and MEAN stack apps in the future.

Since Express has a such a large presence in our Node applications, let's take a look at how we can use the new features in our applications, specifically the Router.

Overview
Express 4.0 comes with the new Router. Router is like a mini express application. It doesn't bring in views or settings, but provides us with the routing APIs like .use, .get, .param, and route.

Let's look at how many of us route our applications and let's see how we can recreate that with Router.

Our Sample Application
Let's create an application that has some routes and a few features. Let's run through those now.

Basic Routes: Home, About
Route Middleware to log requests to the console
Route with Parameters
Route Middleware for Parameters to validate specific parameters
Login routes Doing a GET and POST on /login
Validates a parameter passed to a certain route
Application Structure
We'll only need two files for our application.


- package.json  // set up our node packages
- server.js     // set up our app and build routes

We will house our routes in the server.js file. In the future we'll want to move these out into their own files to keep our application modular. We can even define different route files for different sections of our site.

Starting Our Application
Let's start up our Node application. We will need our package.json file to define our dependencies.



{
    "name": "express-router-experiments",
    "main": "server.js",
    "dependencies": {
        "express": "~4.0.0"
    }
}

We'll only need one dependency, Express! Pretty sweet to see that 4.0.0 after seeing 3.x.x for so long.

React LogoReact Logo
UPGRADE YOUR JS
Go from vanilla JavaScript 👉 React
Watch for FREE
Go ahead and install our dependencies.


$ npm install

Now we have Express. Let's look at starting up our application and then we can handle our routing.

Creating Our Server
We will use Express to start our application server. Since we defined server.js as the main file in package.json, that is the file that Node will use. Let's define that file now.

// server.js

// BASE SETUP
// ==============================================

var express = require('express');
var app     = express();
var port    =   process.env.PORT || 8080;

// ROUTES
// ==============================================

// sample route with a route the way we're used to seeing it
app.get('/sample', function(req, res) {
    res.send('this is a sample!');  
});

// we'll create our routes here

// START THE SERVER
// ==============================================
app.listen(port);
console.log('Magic happens on port ' + port);

Now we can start our server. We've created a route using the normal app.get that we've used in our Express 3.0 applications. If we go into our browser and visit http://localhost:8080/sample, we will be able to see this is a sample!. Now we'll move to creating routes using the Express 4.0 Router.

Express Router
What exactly is the Express Router? It is a mini express application without all the bells and whistles of an express application, just the routing stuff. Let's take a look at exactly what this means. We'll go through each section of our site and use different features of the Router.

Basic Routes express.Router()
Let's call an instance of the Router for creating our frontend routes for our application. This will include the Home and About pages.

// server.js

...

// we'll create our routes here

// get an instance of router
var router = express.Router();

// home page route (http://localhost:8080)
router.get('/', function(req, res) {
    res.send('im the home page!');  
});

// about page route (http://localhost:8080/about)
router.get('/about', function(req, res) {
    res.send('im the about page!'); 
});

// apply the routes to our application
app.use('/', router);

...

We will call an instance of the express.Router(), apply routes to it, and then tell our application to use those routes. We can now access the home page at http://localhost:8080 and the about page at http://localhost:8080/about.

Notice how we can set a default root for using these routes we just defined. If we had changed line 21 to app.use('/app', router), then our routes would be http://localhost:8080/app and http://localhost:8080/app/about.

This is very powerful because we can create multiple express.Router()s and then apply them to our application. We could have a Router for our basic routes, authenticated routes, and even API routes.

Using the Router, we are allowed to make our applications more modular and flexible than ever before by creating multiple instances of the Router and applying them accordingly. Now we'll take a look at how we can use middleware to handle requests.

Route Middleware router.use()
Route middleware in Express is a way to do something before a request is processed. This could be things like checking if a user is authenticated, logging data for analytics, or anything else we'd like to do before we actually spit out information to our user.

Here is some middleware to log a message to our console every time a request is made. This will be a demonstration of how to create middleware using the Express Router.

// server.js

...

// we'll create our routes here

// get an instance of router
var router = express.Router();

// route middleware that will happen on every request
router.use(function(req, res, next) {

    // log each request to the console
    console.log(req.method, req.url);

    // continue doing what we were doing and go to the route
    next(); 
});

// home page route (http://localhost:8080)
router.get('/', function(req, res) {
    res.send('im the home page!');  
});

// about page route (http://localhost:8080/about)
router.get('/about', function(req, res) {
    res.send('im the about page!'); 
});

// apply the routes to our application
app.use('/', router);

...

We'll use router.use() to define middleware. This will now be applied to all of the requests that come into our application for this instance of Router. Let's go into our browser and go to http://localhost:8080 and we'll see the request in our console.

express-router-console-log-request
The order you place your middleware and routes is very important. Everything will happen in the order that they appear. This means that if you place your middleware after a route, then the route will happen before the middleware and the request will end there. Your middleware will not run at that point.

Keep in mind that you can use route middleware for many things. You can use it to check that a user is logged in in the session before letting them continue.

Route with Parameters /hello/:name
Let's say we wanted to have a route called /hello/:name where we could pass in a person's name into the URL and the application would spit out Hello *name*!. Let's create that route now.

// server.js

...

// we'll create our routes here

// get an instance of router
var router = express.Router();

...

// route with parameters (http://localhost:8080/hello/:name)
router.get('/hello/:name', function(req, res) {
    res.send('hello ' + req.params.name + '!');
});

// apply the routes to our application
app.use('/', router);

...

Now we can visit http://localhost:8080/hello/holly and see our browser spit out hello holly! Easy cheese.

express-router-parameters
Now let's say we wanted to validate this name somehow. Maybe we'd want to make sure it wasn't a curse word. We would do that validation inside of route middleware. We'll use a special middleware for this.

Route Middleware for Parameters
We will use Express's .param() middleware. This creates middleware that will run for a certain route parameter. In our case, we are using :name in our hello route. Here's the param middleware.

// server.js

...

// we'll create our routes here

// get an instance of router
var router = express.Router();

...

// route middleware to validate :name
router.param('name', function(req, res, next, name) {
    // do validation on name here
    // blah blah validation
    // log something so we know its working
    console.log('doing name validations on ' + name);

    // once validation is done save the new item in the req
    req.name = name;
    // go to the next thing
    next(); 
});

// route with parameters (http://localhost:8080/hello/:name)
router.get('/hello/:name', function(req, res) {
    res.send('hello ' + req.name + '!');
});

// apply the routes to our application
app.use('/', router);

...

Now when we hit the /hello/:name route, our route middleware will kick in and be used. We can run validations and then we'll pass the new variable to our .get route by storing it in req. We then access it by changing req.params.name to req.name.

When we visit our browser at http://localhost:8080/hello/sally we'll see our request logged to the console.

express-router-parameter-middleware
Route middleware for parameters can be used to validate data coming to your application. If you have created a RESTful API also, you can validate a token and make sure the user is able to access your information.

The last thing we'll look at today is how to use app.route() to define multiple routes.

Login Routes app.route
We can define our routes right on our app. This is similar to using app.get, but we will use app.route. app.route is basically a shortcut to call the Express Router. Instead of calling express.Router(), we can call app.route and start applying our routes there.

Using app.route lets us define multiple actions on a single login route. We'll need a GET route to show the login form and a POST route to process the login form.



...

// ROUTES
// ==============================================

app.route('/login')

    // show the form (GET http://localhost:8080/login)
    .get(function(req, res) {
        res.send('this is the login form');
    })

    // process the form (POST http://localhost:8080/login)
    .post(function(req, res) {
        console.log('processing');
        res.send('processing the login form!');
    });

...

Now we have defined our two different actions on our /login route. Simple and very clean.

Conclusion
With the inclusion of the Express 4.0 Router, we are given more flexibility than ever before in defining our routes. To recap, we can:

Use express.Router() multiple times to define groups of routes
Apply the express.Router() to a section of our site using app.use()
Use route middleware to process requests
Use route middleware to validate parameters using .param()
Use app.route() as a shortcut to the Router to define multiple requests on a route
With all the ways we can define routes, I'm sure that our applications will benefit going forward. Sound off in the comments if you have any questions or suggestions.

Like this article? Follow @chrisoncode on Twitter








Resource: https://expressjs.com/en/guide/routing.html
Resource: 