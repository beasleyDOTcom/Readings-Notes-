# 401 Advanced Software Development in Full Stack Javascript
## day 2 
#### Name 3 advantages to Test Driven Development
- Writing the tests first requires you to really consider what do you want from the code.
- You receive fast feedback.
- TDD creates a detailed specification and reduces time spent on rework.
RESOURCE: https://dzone.com/articles/20-benefits-of-test-driven-development

#### In what case would you need to use beforeEach() or afterEach() in a test suite?
If you have some work you need to do repeatedly for many tests, you can use beforeEach and afterEach.

For example, let's say that several tests interact with a database of cities. You have a method initializeCityDatabase() that must be called before each of these tests, and a method clearCityDatabase() that must be called after each of these tests. You can do this with:

beforeEach(() => {
  initializeCityDatabase();
});

afterEach(() => {
  clearCityDatabase();
});

test('city database has Vienna', () => {
  expect(isCity('Vienna')).toBeTruthy();
});

test('city database has San Juan', () => {
  expect(isCity('San Juan')).toBeTruthy();
});

Copy
beforeEach and afterEach can handle asynchronous code in the same ways that tests can handle asynchronous code - they can either take a done parameter or return a promise. For example, if initializeCityDatabase() returned a promise that resolved when the database was initialized, we would want to return that promise:

beforeEach(() => {
  return initializeCityDatabase();
});

RESOURCE: https://jestjs.io/docs/en/setup-teardown

#### What is one downside of Test Driven Development
It necessitates a lot of time and effort up front, which can make development feel slow to begin with.
Focusing on the simplest design now and not thinking ahead can mean major refactoring requirements.
It's difficult to write good tests that cover the essentials and avoid the superfluous.
RESOURCE: https://leantesting.com/test-driven-development/
#### What’s the primary difference between ES6 Classes and Constructor/Prototype Classes?
They work the say way under the hood. They main difference is readability and ease of learning for those switching over from other programming languages. Not to mention that it's much easier and less comfusing to write. 
#### Name a use case for a static method
when using a count.
#### Write an example of a Higher Order function and describe the use case it solves
.filter() and .map() both take callback functions and iterate over each item in an object/array and applying the callback functino to the current value;

### Document the following Vocabulary Terms
##### functional programming:
Functional programming is the process of building software by composing pure functions, avoiding shared state, mutable data, and side-effects. Functional programming is declarative (telling the computer what you want to do) rather than imperative (telling the computer exactly how to do that), and application state flows through pure functions. Contrast it with object-oriented programming, where application state is usually shared and co-located with methods in objects.

Why Functional Programming?
It’s generally more concise
It’s generally more predictable
It’s easier to test than object-oriented code
RESOURCE: https://www.freecodecamp.org/news/intro-to-functional-programming-basics/
##### pure function
A pure function is one that passes these two tests: 
it must produce no side effects(no mutating).
given the same input, it must return the same output every single time.
this makes it predictable and easily testable.
RESOURCE: https://www.freecodecamp.org/news/what-is-a-pure-function-in-javascript-acb887375dfe/
##### higher-order function
Higher-order functions are a big part of functional programming. A higher-order function is a function that either takes a function(s) as a parameter or returns a function.
RESOURCE:  https://www.freecodecamp.org/news/intro-to-functional-programming-basics/
##### immutable state
I'm not sure about this one.. constants?
##### object
an object is a value type that is based on a system of key: value pairs. 
##### object-oriented programming (OOP)
Object-oriented programming (OOP) is a programming paradigm based on the concept of "objects", which can contain data, in the form of fields (often known as attributes or properties), and code, in the form of procedures (often known as methods). A feature of objects is that an object's own procedures can access and often modify the data fields of itself (objects have a notion of "this" or "self"). In OOP, computer programs are designed by making them out of objects that interact with one another.[1][2] OOP languages are diverse, but the most popular ones are class-based, meaning that objects are instances of classes, which also determine their types.
RESOURCE: https://en.wikipedia.org/wiki/Object-oriented_programming
##### class
lasses are a template for creating objects. They encapsulate data with code to work on that data. Classes in JS are built on prototypes but also have some syntax and semantics that are not shared with ES5 classalike semantics.
RESOURCE: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes#:~:text=Classes%20are%20a%20template%20for,shared%20with%20ES5%20classalike%20semantics.
##### prototype
A prototype is a method of a class/constructor
##### super
aThe super keyword is used to call corresponding methods of super class. This is one advantage over prototype-based inheritance.
resource: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes#Super_class_calls_with_super
##### inheritance
inheritance communicates the relationship between sub and superclasses
##### constructor
a constructor is a function that is used to instantiate objects/normalize data, and reduce the volume of visible code.
##### instance
everytime new is called with a constructor function a new "instance" of that constructor is made.
##### context 
referse to the goings on in and around the code you are writing.
##### this
this refers to the instance that the use of "new" generated.
##### Test Driven Development (TDD)
Test-driven development (TDD) is a software development process that relies on the repetition of a very short development cycle: requirements are turned into very specific test cases, then the code is improved so that the tests pass.
RESOURCE: https://en.wikipedia.org/wiki/Test-driven_development
##### Jest
Jest is a testing language.
##### Continuous Integration (CI)
Continuous integration (CI) is the practice of automating the integration of code changes from multiple contributors into a single software project. The CI process is comprised of automatic tools that assert the new code’s correctness before integration. A source code version control system is the crux of the CI process. The version control system is also supplemented with other checks like automated code quality tests, syntax style review tools, and more.  
RESOURCE: https://www.atlassian.com/continuous-delivery/continuous-integration
##### unit test
In computer programming, unit testing is a software testing method by which individual units of source code—sets of one or more computer program modules together with associated control data, usage procedures, and operating procedures—are tested to determine whether they are fit for use.
RESOURCE: https://en.wikipedia.org/wiki/Unit_testing