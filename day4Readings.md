### Why would a developer choose to make data models?
to help your future self or whoever else may be tasked with updating the app or system that is being worked on.
### What purpose do CRUD operations serve?
create, read, update, delete.
### What kind of database is Postgres? What kind of database is MongoDB?
Postgres is a object relational database that relies on SQl commands. MongoDB is a document oriented database that uses it's own set of commands that handles a lot of the complication for you.
### What is Mongoose and why do we need it?
mongoose is document relational database and that allows us to work with data that, perhaps we don't know the exact shape of just yet. 
### Describe how NoSQL Databases scale horizontally
by adding tables that aren't deeper and deeper but instead stay more like a one dimensional array?
### Give one strong argument for and against NoSQL Databases
NoSQL databases are easier/simpler to work with and allow you to be less specific about what you want to get and store, but with that ease comes  a complication of specificity when you try and tether tables for example. 
### Define three related pieces of data in a possible application. An example for a store application might be Product, Category and Department. Describe the constraints and rules on each piece of data and how you would relate these pieces to each other. For example, each Product has a Category and belongs in a Department.
These would be prototypical in a class based system where you would have inheritence. Inheritence speaking to the relationship between objects describing that the piece of data might belong to a product that is a child of child department of a child store etc.
### Name 3 cloud based NoSQL Databases
bitnami
scaleGrid
heroku
RESOURCE: https://handsontable.com/blog/articles/2016/12/top-9-nosql-cloud-platforms-to-store-your-data
# Document the following Vocabulary Terms
Term

### database
A database is an organized collection of data, generally stored and accessed electronically from a computer system. Where databases are more complex they are often developed using formal design and modeling techniques.
RESOURECE: https://en.wikipedia.org/wiki/Database
### data model
A data model (or datamodel)[1][2][3][4][5] is an abstract model that organizes elements of data and standardizes how they relate to one another and to the properties of real-world entities. For instance, a data model may specify that the data element representing a car be composed of a number of other elements which, in turn, represent the color and size of the car and define its owner.

The term data model can refer to two distinct but closely related concepts. Sometimes it refers to an abstract formalization of the objects and relationships found in a particular application domain: for example the customers, products, and orders found in a manufacturing organization. At other times it refers to the set of concepts used in defining such formalizations: for example concepts such as entities, attributes, relations, or tables. So the "data model" of a banking application may be defined using the entity-relationship "data model". This article uses the term in both senses.


Overview of a data-modeling context: Data model is based on Data, Data relationship, Data semantic and Data constraint. A data model provides the details of information to be stored, and is of primary use when the final product is the generation of computer software code for an application or the preparation of a functional specification to aid a computer software make-or-buy decision. The figure is an example of the interaction between process and data models.[6]
A data model explicitly determines the structure of data. Data models are typically specified by a data specialist, data librarian, or a digital humanities scholar in a data modeling notation. These notations are often represented in graphical form.[7]

A data model can sometimes be referred to as a data structure, especially in the context of programming languages. Data models are often complemented by function models, especially in the context of enterprise models.
RESOURCE: https://en.wikipedia.org/wiki/Data_model
### CRUD
create, read, update, delete.
### schema
a schema is essentially a template for your database that defines the input.
### sanitize
we sanitize data in order to:
prevent code injection problems, utilize secure input and output handling, such as:

Using APIs that, if used properly, are secure against all input characters. Parameterized queries (also known as "Compiled queries", "prepared statements", "bound variables") allows for moving user data out of string to be interpreted. Additionally Criteria API[7] and similar APIs move away from the concept of command strings to be created and interpreted.
Enforcing language separation via a static type system.[8]
Input validation, such as whitelisting only known good values, this can be done on client side using JavaScript for example or it can be done on the server side which is more secure.
Input encoding, e.g. escaping dangerous characters. For instance, in PHP, using the htmlspecialchars() function to escape special characters for safe output of text in HTML, and mysqli::real_escape_string() to isolate data which will be included in an SQL request, to protect against SQL Injection.
Output encoding, i.e. preventing HTML Injection (XSS) attacks against web site visitors
HttpOnly is a flag for HTTP Cookies that, when set, does not allow client-side script interaction with cookies, thereby preventing certain XSS attacks.[9]
Modular shell disassociation from kernel
With SQL Injection, one can use parameterized queries, stored procedures, whitelist input validation, and more to help mitigate Code Injection problems.[10]
The solutions listed above deal primarily with web-based injection of HTML or script code into a server-side application. Other approaches must be taken, however, when dealing with injection of user code on the user machine, resulting in privilege elevation attacks. Some approaches that are used to detect and isolate managed and unmanaged code injections are:

Runtime image hash validation – capture a hash of a part or complete image of the executable loaded into memory, and compare it with stored and expected hash.
NX bit – all user data is stored in a special memory sections that are marked as non-executable. The processor is made aware that no code exists in that part of memory, and refuses to execute anything found in there.
Canaries – randomly place values in a stack. At runtime, a canary is checked when a function returns. If a canary has been modified, the program stops execution and exits. This occurs on a Stack Overflow Attack.
[In C]Code Pointer Masking (CPM) – after loading a (potentially changed) code pointer into a register, apply a bitmask to the pointer. This effectively restricts the addresses to which the pointer can refer.[11]
resource: https://en.wikipedia.org/wiki/Code_injection#Preventing_problems
### Structured Query Language (SQL)
SQL is a domain-specific language used in programming and designed for managing data held in a relational database management system, or for stream processing in a relational data stream management system.
resource: https://en.wikipedia.org/wiki/SQL
### Non SQL (NoSQL)
A NoSQL database provides a mechanism for storage and retrieval of data that is modeled in means other than the tabular relations used in relational databases. Such databases have existed since the late 1960s, but the name "NoSQL" was only coined in the early 21st century, triggered by the needs of Web 2.0 companies.
resource: https://en.wikipedia.org/wiki/NoSQL
### MongoDB
MongoDB is a cross-platform document-oriented database program. Classified as a NoSQL database program, MongoDB uses JSON-like documents with optional schemas. MongoDB is developed by MongoDB Inc. and licensed under the Server Side Public License.
resource: https://en.wikipedia.org/wiki/MongoDB
### Mongoose
Mongoose is an Object Data Modeling (ODM) library for MongoDB and Node.js. It manages relationships between data, provides schema validation, and is used to translate between objects in code and the representation of those objects in MongoDB.
resource: https://www.freecodecamp.org/news/introduction-to-mongoose-for-mongodb-d2a7aa593c57/
### record
In computer science, a record is a basic data structure. Records in a database or spreadsheet are usually called "rows". A record is a collection of fields, possibly of different data types, typically in fixed number and sequence. Wikipedia
RESOURCE: https://en.wikipedia.org/wiki/Record_(computer_science)
### document
‘Documents’ are equivalent to records or rows of data in SQL. While a SQL row can reference data in other tables, Mongo documents usually combine that in a document.
resource: https://www.freecodecamp.org/news/introduction-to-mongoose-for-mongodb-d2a7aa593c57/
### Object Relation Mapping (ORM)
Object-relational mapping in computer science is a programming technique for converting data between incompatible type systems using object-oriented programming languages. This creates, in effect, a "virtual object database" that can be used from within the programming language.
resource: https://en.wikipedia.org/wiki/Object-relational_mapping