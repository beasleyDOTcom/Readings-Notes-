## Why would a developer choose to make data models?
A data model helps design the database at the conceptual, physical and logical levels. Data Model structure helps to define the relational tables, primary and foreign keys and stored procedures. It provides a clear picture of the base data and can be used by database developers to create a physical database.
RESOURCE https://www.guru99.com/data-modelling-conceptual-logical.html#:~:text=A%20data%20model%20helps%20design,to%20create%20a%20physical%20database.
## What purpose do CRUD operations serve?
create, read, update and delete
## What kind of database is Postgres? What kind of database is MongoDB?
postgress is a spl database and mongoDB is a nosql database.
Also, mongo is document oriented instead of object relational. (to have the most consisent results you need to know the shape of the object)
## What is Mongoose and why do we need it?
mongoose is document relational database and that allows us to work with data that, perhaps we don't know the exact shape of just yet. 
## Describe how NoSQL Databases scale horizontally
Relational database or RDBMS databases are vertically Scalable When load increase on RDBMS database then we scale database by increasing server hardware power ,need to by expensive and bigger servers and NoSQL databases are designed to expand horizontally and in Horizontal scaling means that you scale by adding more machines into your pool of resources.
RESOURCE: https://www.loginradius.com/engineering/blog/relational-database-management-system-rdbms-vs-nosql/#:~:text=Relational%20database%20or%20RDBMS%20databases,you%20scale%20by%20adding%20more
## Give one strong argument for and against NoSQL Databases
#### FOR

NoSQL databases allow seasoned programmers, who are well aware of race-conditions and atomic operations, to forego a large amount of processing only required in a small percentage of today's web application code. NoSQL databases certainly have atomic operations and most all transactional requirements present in SQL databases can also be obtained NoSQL databases. The difference is the level of abstraction. NoSQL databases remove the higher levels of abstraction and hand that capability to the application programmer, thereby resulting is faster code overall with the increased probability of data corruption by unseasoned programmers.

As a result we are much more likely to see NoSQL databases being used more and more heavily in the web application space, where development time and performance are very important. Financial and corporate software is likely to retain it's SQL heritage because hardware performance is relatively cheap, they have seasoned DBAs on-hand, and the increased risk caused by unseasoned programmers is not palatable.
RESOURCE: https://softwareengineering.stackexchange.com/questions/194340/why-are-nosql-databases-more-scalable-than-sql
#### AGAINST
NoSQL database is Open Source and Open Source at its greatest strength but at the same time its greatest weakness because there are not many defined standards for NoSQL databases, so no two NoSQL databases are equal
No Stored Procedures in mongodb (NoSql database).
GUI mode tools to access the database is not flexibly available in market
too difficult for finding nosql experts because it is latest technology and NoSQL developer are in learning mode
RESOURCE:https://www.loginradius.com/engineering/blog/relational-database-management-system-rdbms-vs-nosql/#:~:text=Relational%20database%20or%20RDBMS%20databases,you%20scale%20by%20adding%20more
BY https://softwareengineering.stackexchange.com/users/87727/randomprogrammer
## Define three related pieces of data in a possible application. An example for a store application might be Product, Category and Department. Describe the constraints and rules on each piece of data and how you would relate these pieces to each other. For example, each Product has a Category and belongs in a Department.
this questions confuses me and I don't know what it's looking for even though it provided an example.

## Name 3 cloud based NoSQL Databases
bitnami
scaleGrid
heroku
RESOURCE: https://handsontable.com/blog/articles/2016/12/top-9-nosql-cloud-platforms-to-store-your-data
## Document the following Vocabulary Terms
## Term
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
CREATE, READ, UPDATE, DELETE
### schema
The schema defines the data you will be sending into the database so that it knows what to expect and how to handle it.
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
### document
‘Documents’ are equivalent to records or rows of data in SQL. While a SQL row can reference data in other tables, Mongo documents usually combine that in a document.
resource: https://www.freecodecamp.org/news/introduction-to-mongoose-for-mongodb-d2a7aa593c57/
### Object Relation Mapping (ORM)
Object-relational mapping in computer science is a programming technique for converting data between incompatible type systems using object-oriented programming languages. This creates, in effect, a "virtual object database" that can be used from within the programming language.
resource: https://en.wikipedia.org/wiki/Object-relational_mapping