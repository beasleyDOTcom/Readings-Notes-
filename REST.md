# HTTP
HTTP Requests
A HTTP/1.1 request is formatted in text and transferred using TCP. The first line of the request contains the METHOD, URL, and HTTP VERSION. The following lines are the request HEADERS. Each header is separated by a newline character. A header is a key value pair separated using a colon. Headers containing more than one value separate each value using a semicolon. The header section of the request is terminated with an empty line. An optional body follows the header section.

HTTP Method	Request Has Body	Response Has Body	Safe	Idempotent	Cacheable	Function
GET	No	Yes	Yes	Yes	Yes	Retrieve a resource
HEAD	No	No	Yes	Yes	Yes	Like GET but headers only
POST	Yes	Yes	No	No	Yes	Create a resource
PUT	Yes	Yes	No	Yes	No	Update a resource
DELETE	No	Yes	No	Yes	No	Delete a resource
CONNECT	Yes	Yes	No	No	No	Create TCP/IP tunnel
OPTIONS	Optional	Yes	Yes	Yes	No	Returns supported methods for a URL
TRACE	No	Yes	Yes	Yes	No	Echos retrieved request
PATCH	Yes	Yes	No	No	No	Partial modification of resource
Safe methods should only be used for information retrieval and should not change the server state. Idempotent methods means if two identical requests are made they should get an identical response. Cacheable means the client should be able to cache the response.

# REST 
- REST Method	CRUD Operation	Function
- GET	READ	Retrieve 1 or More Records
- POST	CREATE	Create a new record
 - PUT	UPDATE	Update a record through  replacement (Put it back)
- PATCH	UPDATE	Update a record (just the parts that changed)
- DESTROY	DELETE	Remove a record


### Generating your own Swagger Documentation
The swagger documentation service allows you to generate the swagger documentation simply by visiting your API and analyzing the output.

Visit and review the docs and overview at Swagger.io
Sign in to the Swagger Inspector
Visit your API, using all applicable REST endpoints and data
Note that on the right side, it’ll keep your history
Once you’ve gone through all of your routes, use the radio buttons select the routes you want to document
Click the “Create API Definition” button
Follow the instructions to import your new API documentation to Swagger Hub
You can leave it running there, or download the definition as .yml or .json and use it in your own project

## summary
Today's readings are about taking a closer look at how HTTP and RESTful API's work. 
a good section of this reading is about the type of requests being made and the information that can be included in that request. For Example, a HEAD method doesn't contain a BODY. 
and SWAGGER is a tool for documenting API's.