# 401 quick reference definitions
### Why would you want to run JavaScript code outside of a browser?
development purposes i.e. building, testing, apps, functions, etc.  
### What is the difference between a module and a package?
#### Package 
A package is a file or directory that is described by a package.json file. A package must contain a package.json file in order to be published to the npm registry.
A package is any of the following:

a) A folder containing a program described by a package.json file.
b) A gzipped tarball containing (a).
c) A URL that resolves to (b).
d) A <name>@<version> that is published on the registry with (c).
e) A <name>@<tag> that points to (d).
f) A <name> that has a latest tag satisfying (e).
g) A git url that, when cloned, results in (a).
#### Module
A module is any file or directory in the node_modules directory that can be loaded by the Node.js require() function.

To be loaded by the Node.js require() function, a module must be one of the following:

A folder with a package.json file containing a "main" field.
A folder with an index.js file in it.
A JavaScript file.
Note: Since modules are not required to have a package.json file, not all modules are packages. Only modules that have a package.json file are also packages.
In the context of a Node program, the module is also the thing that was loaded from a file. For example, in the following program:

var req = require('request')
we might say that “The variable req refers to the request module”.

### What does the node package manager do?
NPM allows you to easily download and use differen't packages or libraries for use in your project. 

npm, short for Node Package Manager, is two things: first and foremost, it is an online repository for the publishing of open-source Node.js projects; second, it is a command-line utility for interacting with said repository that aids in package installation, version management, and dependency management. A plethora of Node.js libraries and applications are published on npm, and many more are added every day. These applications can be searched for on http://npmjs.org/. Once you have a package you want to install, it can be installed with a single command-line command.

### Provide code snippets showing 3 different ways to export a function from a node 
You can export a function or multiple functions by exporting an object with key/value pairs that corelate to the different functions.
for example, 
function debbie(){
console.log('great singer songwriter')
}
function miller(){
    console.log('haha')
}
module.exports = {
    debbie: debbie,
    miller:miller
}
then you assign it and use it.
let libraryFonk = require('path to that info')
console.log(libraryFonk.debbie() + libraryFonk.miller())

#### or as a class
module.exports = function (firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.fullName = function () { 
        return this.firstName + ' ' + this.lastName;
    }
}
var person = require('./Person.js');

var person1 = new person('James', 'Bond');

console.log(person1.fullName());
#### or as a export function
module.exports = function (msg) { 
    console.log(msg);
};
var msg = require('./Log.js');

msg('Hello World');

## terms and definitions:
#### ecosystem: 
In the context of software analysis, the term software ecosystem is defined by Lungu [6] as “a collection of software projects, which are developed and co-evolve in the same environment”. The environment can be organizational (a company), social (an open-source community), or technical (the Ruby ecosystem). The ecosystem metaphor is used in order to denote an analysis which takes into account multiple software systems.[7] The most frequent of such analyses is static analysis of the source code of the component systems of the ecosystem.
#### node.js
Node.js is an open-source, cross-platform, JavaScript runtime environment (Framework) that executes JavaScript code outside a web browser. Node.js lets developers use JavaScript to write command line tools and for server-side scripting—running scripts server-side to produce dynamic web page content before the page is sent to the user's web browser. Consequently, Node.js represents a "JavaScript everywhere" paradigm,[6] unifying web-application development around a single programming language, rather than different languages for server- and client-side scripts.

Though .js is the standard filename extension for JavaScript code, the name "Node.js" doesn't refer to a particular file in this context and is merely the name of the product. Node.js has an event-driven architecture capable of asynchronous I/O. These design choices aim to optimize throughput and scalability in web applications with many input/output operations, as well as for real-time Web applications (e.g., real-time communication programs and browser games)
#### V8 Engine
V8 is a powerful open source Javascript engine provided by Google. So what actually is a Javascript Engine? It is a program that converts Javascript code into lower level or machine code that microprocessors can understand.
#### module
A module is any file or directory in the node_modules directory that can be loaded by the Node.js require() function.

To be loaded by the Node.js require() function, a module must be one of the following:

A folder with a package.json file containing a "main" field.
A folder with an index.js file in it.
A JavaScript file.
Note: Since modules are not required to have a package.json file, not all modules are packages. Only modules that have a package.json file are also packages.
In the context of a Node program, the module is also the thing that was loaded from a file. For example, in the following program:

var req = require('request')
we might say that “The variable req refers to the request module”.
#### Package 
A package is a file or directory that is described by a package.json file. A package must contain a package.json file in order to be published to the npm registry.
A package is any of the following:

a) A folder containing a program described by a package.json file.
b) A gzipped tarball containing (a).
c) A URL that resolves to (b).
d) A <name>@<version> that is published on the registry with (c).
e) A <name>@<tag> that points to (d).
f) A <name> that has a latest tag satisfying (e).
g) A git url that, when cloned, results in (a).
#### node package manager
NPM allows you to easily download and use differen't packages or libraries for use in your project. 

npm, short for Node Package Manager, is two things: first and foremost, it is an online repository for the publishing of open-source Node.js projects; second, it is a command-line utility for interacting with said repository that aids in package installation, version management, and dependency management. A plethora of Node.js libraries and applications are published on npm, and many more are added every day. These applications can be searched for on http://npmjs.org/. Once you have a package you want to install, it can be installed with a single command-line command.
#### server
Server (computing), a computer program or a device that provides functionality for other programs or devices, called clients
#### environment
Environment (type theory), the association between variables names and data types in type theory
Deployment environment, in software deployment, a computer system in which a computer program or software component is deployed and executed
Runtime environment, a virtual machine state which provides software services for processes or programs while a computer is running
#### interpreter
In computer science, an interpreter is a computer program that directly executes instructions written in a programming or scripting language, without requiring them previously to have been compiled into a machine language program. An interpreter generally uses one of the following strategies for program execution:

Parse the source code and perform its behavior directly;
Translate source code into some efficient intermediate representation and immediately execute this;
Explicitly execute stored precompiled code[1] made by a compiler which is part of the interpreter system.
Early versions of Lisp programming language and Dartmouth BASIC would be examples of the first type. Perl, Python, MATLAB, and Ruby are examples of the second, while UCSD Pascal is an example of the third type. Source programs are compiled ahead of time and stored as machine independent code, which is then linked at run-time and executed by an interpreter and/or compiler (for JIT systems). Some systems, such as Smalltalk and contemporary versions of BASIC and Java may also combine two and three.[2] Interpreters of various types have also been constructed for many languages traditionally associated with compilation, such as Algol, Fortran, Cobol, C and C++.

While interpretation and compilation are the two main means by which programming languages are implemented, they are not mutually exclusive, as most interpreting systems also perform some translation work, just like compilers. The terms "interpreted language" or "compiled language" signify that the canonical implementation of that language is an interpreter or a compiler, respectively. A high level language is ideally an abstraction independent of particular implementations.
#### compiler
In computing, a compiler is a computer program that translates computer code written in one programming language (the source language) into another language (the target language). The name "compiler" is primarily used for programs that translate source code from a high-level programming language to a lower level language (e.g., assembly language, object code, or machine code) to create an executable program.[1][2]:p1

There are many different types of compilers. If the compiled program can run on a computer whose CPU or operating system is different from the one on which the compiler runs, the compiler is a cross-compiler. A bootstrap compiler is written in the language that it intends to compile. A program that translates from a low-level language to a higher level one is a decompiler. A program that translates between high-level languages is usually called a source-to-source compiler or transcompiler. A language rewriter is usually a program that translates the form of expressions without a change of language. The term compiler-compiler refers to tools used to create parsers that perform syntax analysis.

A compiler is likely to perform many or all of the following operations: preprocessing, lexical analysis, parsing, semantic analysis (syntax-directed translation), conversion of input programs to an intermediate representation, code optimization and code generation. Compilers implement these operations in phases that promote efficient design and correct transformations of source input to target output. Program faults caused by incorrect compiler behavior can be very difficult to track down and work around; therefore, compiler implementers invest significant effort to ensure compiler correctness.[3]

Compilers are not the only language processor used to transform source programs. An interpreter is computer software that transforms and then executes the indicated operations.[2]:p2 The translation process influences the design of computer languages, which leads to a preference of compilation or interpretation. In practice, an interpreter can be implemented for compiled languages and compilers can be implemented for interpreted languages.
### Resources used: 
https://docs.npmjs.com/about-packages-and-modules
https://www.youtube.com/watch?v=4jceJ4APdQk
https://nodejs.org/en/knowledge/getting-started/npm/what-is-npm/#:~:text=npm%20%2C%20short%20for%20Node%20Package,version%20management%2C%20and%20dependency%20management
https://www.tutorialsteacher.com/nodejs/nodejs-module-exports
https://en.wikipedia.org/wiki/Node.js
https://en.wikipedia.org/wiki/Software_ecosystem#:~:text=In%20the%20context%20of%20software,technical%20(the%20Ruby%20ecosystem).
https://www.freecodecamp.org/news/understanding-the-core-of-nodejs-the-powerful-chrome-v8-engine-79e7eb8af964/#:~:text=Now%20back%20to%20the%20V8,code%20that%20microprocessors%20can%20understand
https://en.wikipedia.org/wiki/Server
https://en.wikipedia.org/wiki/Environment
https://en.wikipedia.org/wiki/Interpreter_(computing)
https://en.wikipedia.org/wiki/Compiler