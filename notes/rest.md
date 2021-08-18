REST is a simple way to organise interactions between independent systems.
REST allows you to interact with minimal overhead with clients as diverse as mobile phones and other websites.
REST is not tied to the web, but it's almost always implemented as such, and was inspired by HTTP. As a result, REST can be used wherever HTTP can.

Because REST has been inspired by HTTP and plays to its strenghts, it is best the best way to learn how HTTP works.

HTTP is the protocol that allows for sending documents back and forth on the web.
In HTTP, there are two different roles: server and client.
In general, the client always initiates the conversation; the server replies.
HTTP messages are made of a header and a body. The body can often remain empty; it contains data that you want to transmit over the network, in order to use it according to the instructions in the header.
The header contains metadata, such as encoding information; but, in the case of a request, it also contains the important HTTP methods. In the REST style, often the header data is more significant than the body.

With some browser developer tools, you can view the details of HTTP requests as you surf.

Another helpful way to familiarise yourself with HTTP is to use a dedicated client like cURL.
cURL is a command line tool.
`curl -v google.com`
This will display the complete HTTP conversation. Requests begin with `>`, while responses with `<`

URLS are how you identify the things that you want to operate on. Each URL identifies a resource.
The host is included separately from the resource path, which comes right on top of the request header.
GET /clients/alvin HTTP/1.1
HOST: example.com

URLs should be as precise as needed; Everything needed to uniquely identify a resource should be in the url. 

HTTP Verbs
tell the server what to do with the data identified by the URL.
Each request specifies a certain HTTP verb, or method, in the request header. THis is the first all caps word in the request header.
eg.
`GET / HTTP/1.1`
`DELETE /clients/anne HTTP/1.1`

GET
Instructs server to transmit data identified by the URL to client.

PUT
Create or update the resource identified by the URL.
PUT requests contain the data to use in updating or creating the resource in the body.
In cURL, you can add data to the request with the -d switch
`curl -v -X PUT -d "some text"`

DELETE
Delete the resource identified by the URL
`curl -v -X DELETE /clients/anne

POST
When the processing you wish to happen on the server should be repeated, if the POST request is repeated. (not idempotent)
PUT and POST requests can be used easily in place of each other. 

PATCH 
HEAD
OPTIONS
Get the API to tell you itself about possible requests

Safe methods are those that never modify resources. GET is safe, PUT, POST and DELETE are unsafe because they may result in a modification of a resource.

Idempotent methods achieve the same result, no matter how many times the request is repeated. GET, PUT, and DELETE are idempotent. POST is not.

The HTTP client and HTTP server exchange information about resources identified by URLs.

GET
200 Ok
404 Not Found

POST
201 Created
401 Unauthorised
409 Conflict
404 Not Found

PUT and PATCH
200 Ok
401 Unauthorised
404 Not Found
405 Method Not Allowed

PUT updates an existing singleton based on ID
PATCH modifies an existing singleton resource based on ID
PUT replaces content, PATCH gives instructions

DELETEs a singleton resource based on ID
200 Ok
404 Not Found
401 Unauthorised

OPTIONS Get options available for this resource
200 OK

HEAD Get just the response headers for this resource
200 OK 
404 Not Found

Every response from a REST API will have a head section

1xx Information
2xx Success
3xx Redirection
4xx Client Error
5xx Server Error
