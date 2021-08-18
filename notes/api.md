---
layout: post
title: API Design 
date: 2021-05-12
permalink: /notes/api
---

# Learning Rubric

| Level | Attributes |
| ----- | ---------- |
| L1	| Can describe what an API is and what can help make it successful. Has built something that responds to a request locally. Some form of documentation exists. |
| L2	| Can describe the basics of JSON and REST. Understands standard best practices for RESTful API design. The project supports basic operations and this is documented. |
| L3	| Can articulate benefits of following industry stndards for documentation. Project handles all common use-cases including errors. These are documented following industry standards. |
| L4	| Can describe strategies for evolving APIs while minimising customer impact. Has updated project API in such a manner.  |

## What is it?

## Why

Companies have embraced APIs as a way to expose business capabilities to both external and internal developers.
APIs promise the ability to experiment quickly with new business ideas by recombining core capabilities.
Teams that build APIs should understand the needs of their customers (fellow developers/internal system) and make the product compelling to them.
Usability testing and UX research can lead to a better design and understanding of the API usage patterns can help bring a product mindest to APIs
Treat **APIs as a product**
This means they should be actively maintained, supported, and easy to use. They should have an owner who advocates for the customer and strives for continual improvement. 

## Who

## When

## Where

## How

To build a successful API we need to go beyond just the technical implementation.

It needs to be:
* useful
* stable
* secure
* easy to use

We need to treat users as customers, and our API as a product.

C#/dotnetcore
Make sure endpoints have some form of documentation - simple instructions in a README

Commonly see REST over HTTPS using JSON
By following industry standard best practices we can take big steps towards making APIs easier to use for our consumers.



WEB APIs with ASP.NET Core
provide data to different clients
Uniform contract to talk to services

use HTTP verbs
use status codes

Roy Fielding -> Representational State Transfer (REST)
REST is the basis for many APIs.
Design Concept, like a programming paradigm.
Built on top of HTTP
Uses URIs to access resources
Uses HTTP Verbs for operations

REST Constraints:
1. Must have a uniform interface. 
2. Client-Server are independent of each other.
3. Stateless
4. Cacheable (where appropriate)
5. Supports layered system
6. Code on demand

API design basics:
* api.hplussport.com/products
* api.hplussport.com/products/123
* api.hplussport.com/products/123/variants
* api.hplussport.com/products/123/variants/456

Tools for API testing:
Postman -> getpostman.com
F12 Browser dev tools
Fiddler -> telerik.com/fiddler

Controllers and Actions
ControllerBase -> Class to inherit from
[ApiController] -> Class attribute for some convenience features
[HttpGet]/Get() Method and/or attribute to provide the HTTP verb

Routing Basics
Routing with Attributes
|Attribute|Description|
|---------|-----------|
|[Route("/products")]|URL to call the API|
|[Route("/products/{id}")]|Controller action parameter is taken from URL|
|[Route("/products/{id?}")]|Optional controller action parameter is taken from URL|
|[Route("/[controller]")]|Use controller name in URL|

Before implementing actual API, you need to implement the Data Model.

IActionResult
Imagine something goes wrong in db.Products, we should use HTTP status codes.

Handling Errors
200 Ok
204 No Content
404 Not Found
400 Bad Request
307 HTTP Redirect

You can have type validation by putting it in the HttpGet("{id : int}")
If a request doesn't match any routes, it will return a 404

Making the API Asynchronous
[HttpGet]
public **async** **Task** ... {
... **await** db.Products.ToList**Async**();
...
}

Advanced Data Retrieval
* Not always good to return all products, might have so many it takes a while.
* Pagination
.com/products?size=15&page=2
.Take(queryParameters.Size) | .Skip(queryParameters.Size * (queryParameters.Page - 1))
* Filtering
Parameter Class | Where Clause
public decimal? MinPrice {get; set;}
.Where(p => p.Price >= param.MinPrice.Value);
* Searching
.Where(p => p.Name.ToLower().Contains(queryParameters.Name.ToLower()));
* Sorting
.com/products?sortBy=Price&sortOrder=desc
 
Writing Data

REST with HTTP Verbs
|HTTP Verb|Function|
|---------|--------|
|GET|Read data|
|POST|Create new data|
|PUT|Update existing data|
|DELETE|Delete existing data|

PUT and GET are idempotent, do the same thing over and over if you repeat.
POST is not, if you keep repeating it you will have duplicates.

[FromBody]
Data from the body of the HTTP request, mostly POST/PUT
[FromRoute]
Data from the route template
[FromQuery]
Data from the URL

Model Validation
In Startup.cs you can add .ConfigureAPIBehaviorOptions(options => options.SuppressModelStateInvalidFilter = true) to services.AddControllers() so that bad requests default to default requests.
[Required] makes it so properties MUST be set
[MaxLength(255)] sets a max length

Adding Items
[HttpPost]
public async Task<IActionResult> PostProduct(Product product)
{
_context.Products.Add(product);
await _context.SaveChangesAsync();

Updating Items
[HttpPut("{Id}")]
public async Task<IActionResult> PutProduct(int id, [FromBody]Product product)
{
	_context.Entry(product).State = EntityState.Modified;
	await _context.SaveChangesAsync();
	return NoContent();
}
Deleting Items

CRUD (Create, Read, Update, Delete) [Post, Get, Put, Delete]

API Versioning
* HTTP Header
X-API-Version: 1.0
Information may also be part of the Accept HTTP header.

* URL
/v1.0/products
Separates API versions, but gives up the one URI principle

* QueryString
/products?api-version=1.0
Might mix with other URL parameters

Just use Microsoft.AspNetCore.Mvc.Versioning

Using the URL and the above package -> 
[ApiVersion("1.0")]
[Route("v/{v:apiVersion}/products")]
[ApiController]

API Documentation
* Swagger
Framework for API documentation, can also be used to work with the API.
Swagger UI provides a nice interface for APIs (with little work)
https://swagger.io
 
* .Net Core Integration
NSwag.AspNetCore
Swashbuckle.AspNetCore

Securing APIs
* Enforce HTTPS
app.UseHttpsRedirection() in startup.cs
This redirects HTTP requests to HTTPS via 307 HTTP Code

UseHsts() 
Uses HTTP Strict Transport Security to instruct the client to use HTTPS from now on. This does not work for localhost.

CORS (Cross-Origin Resource Sharing)
Server returns Access-Control-Allow-Origin: to client
[EnableCors] on Controller or Action
OR
in Startup.cs -> app.UseCors();

Identity Server, an open source server that does access control.

Swagger
A language agnostic specification for describing REST APIs. Allows computers and humans to understand the capabilities of a REST API without direct access to the source code.
It aims to:
* Minimise the amount of work needed to connect decoupled services
* Reduce the amount of time needed to accurately document a service

The two main OpenAPI implementations for .NET are Swashbuckle and NSwag.

The Swagger project was donated to the OpenAPI initiative in 2015 and has since been referred to as OpenAPI.
OpenAPI refers to the specification. Swagger refers to the family of open-source and commercial products from SmartBear that work with the OpenAPI specification. 

## Rest API Best Practices
Representation State Transfer Application Programming Interfaces are one of the most common kinds of web services available today. They allow various clients to communicate with a server via the REST API.

We should take into account security, performance, and ease of use for API consumers.

A REST API conforms to specific architectural constraints, like stateless communication and cacheable data. It is not protocol or standard. They are most commonly called over HTTPS, but can be accessed through a number of communication protocols.

### Accept and respond with JSON
JSON is the standard for transferring data.
REST APIs should accept JSON for request payload and also send responses to JSON.
set `Content-Type` in the response header to `application/json` after the request is made. Many frameworks do this automatically.

The only exception is if we're trying to send and receive files between client and server.

### Use nouns instead of verbs in endpoint paths
Use nouns which represent the entity that the endpoint that we're retrieving or manipulating as the pathname.

This is because the HTTP request method already has the verb. The action should be indicated by the HTTP request method.
* GET
* POST
* PUT
* DELETE

The verbs map to CRUD operations.

### Name collections with plural nouns
### Nesting resources for hierarchical objects
When designing endpoints, it makes sense to group those that contain associated information. If one object can contain another object, you should design the endpoint to reflect that.
This is good practice regardles of whether your data is structured like this in your database. In fact, it may be advisable to avoid mirroring your database structure in your endpoints to avoid giving attackers unnecessary information.
Eg. .com/articles/:articleId/comments

However, nesting can go too far. Instead, return the URI for that resource.

### Handle errors gracefully and return standard error codes
To eliminate confusion for API users when an error occurs, we should handle errors gracefully and return HTTP response codes that indicate what kind of error occurred. This gives maintainers enough information to understand the problem that's occurred.

Common error HTTP status codes include:
* 400 Bad Request - Client-side input fails validation
* 401 Unauthorised - User is not authorised to access resource
* 403 Forbidden - User is authenticated, but not allowed to access a resource
* 404 Not Found - Resource not found
* 500 Internal Server Error - Generic server error
* 502 Bad Gateway - Invalid response from an upstream server
* 503 Service Unavailable - Something unexpected happened on server side

We should throw errors that correspond to the problem that our app has encountererd.

Error codes need to have messages accompanied with them so that the maintainers have enough information to troubleshoot the issue, but attackers can't use the error content to carry out attacks like stealing information or bringing down the system.

### Allow filtering, sorting, and pagination
The databases behind a REST API can get very large. Sometimes, there's so much data that it shouldn't be returned all at once because it's way too slow or will bring down our systems.

We also need ways to paginate data so that we only return a few results at a time. We don't want to tie up resources for too long by trying to get all requested data at once.

Filtering and pagination increase performance by reducing the usage of server resources. As the database grows, the more important these features are.

### Maintain good security practices
Most communication between client and server should be private since we often send and receive private information. SSL/TLS for security is a must.

A SSL certificate isn't too difficult to load onto a server and the cost is free or very low. There's no reason not to make REST APIs communicate over secured channels instead of in the open.

To enforce the principle of least privilege, we need to add role checks for single roles, or have more granular roles for each user.

If we choose to group users into a few roles, then the roles should have the permissions that cover all they need and no more. If we have more granular permissions for each feature, then we have to make sure admins can add and remove those features from each user. Also, we need to add some preset roles that can be applied to a group of users so that we don't have to do that for every user manually.

### Cache data to improve performance
We can add caching to return data from the local memory cache instead of querying the database to get the data every time we want to retrieve some data that users request. The good thing about caching is that users can get data faster. However, that data may be outdated. This could also lead to issues when debugging in production environments.

If you are using caching, you should also inclued `Cache-Control` information in your headers. This will help users effectively use your caching system.

### Versioning our APIs
We should have different versions of API if we're making any changes to them that may break clients. The versioning can be done according to semantic version like most apps do nowadays.

This way, we can gradually phase out old endpoints instead of forcing everyone to move to the new API at the same time. The v1 endpoint can stay active for people who don't want to change, while the v2, with its shiny new features, can serve those who are ready to upgrade. This is especially important if our API is public. WE should version them so that we won't break third party apps that use our APIs.


https://stackoverflow.blog/2020/03/02/best-practices-for-rest-api-design/

OAuth
OpenId, simple identity layer on top of OAuth, API-friendly

IdentityServer, identity and access control

add nuget package IdentityServer4
Configure clients, users and scopes
set up identityserver in startup.cs


## Parallel Change
Making a change to an interface that impacts all its consumers requires two thinking modes:
* implementing the change itself
* updating all its usages

Parallel change, also known as expand and contract, is a pattern to implement backward-incompatible changes to an interface in a safe manner, by breaking the stage into three distinct phases:
expand
migrate
contract

Expand
augment the interface to support both old and new versions.

Migrate
Update all clients using the old version to the new version.

Contract
Once all usages have been migrated to the new version, remove the old version and change the interface so that it only supports the new version

This pattern is useful when practicing Continuous Delivery because it allows code to be released in any of these three phases. Add deprection notes, documentation, todo notes to help inform clients and other developers working on the same codebase about which version is in the process of being replaced.

Versioning API
When 
APIs only need to be up-versioned when a breaking change is made. Breaking changes include:
* a change in the format of the response data for one or more calls
* a change in the request or response type
* removing any part of the API
Breaking changes should always result in a change to the major version number for an API.
Non-breaking changes, such as adding new endpoints or new response parameters, do not require a change to the major version number. However, it can be helpful to track the minor versions of APIs when changes are made to support customers who may be receiving cached versions of data or may be experiencing other API issues.


https://timdeschryver.dev/blog/how-to-test-your-csharp-web-api
With an integration test, we test the API from the outside out by spinning up the in-memory API client and making an actual HTTP request. I get confidence out of it because I mock as little as possible, and I will consume my API in the same way as an application/user would.

Microsoft.AspNetCore.Mvc.Testing package includes a WebApplicationFactory<TEntryPoint> class which is used to create the API in memory. This is convenient, as we don't need to have the API running before we run these integration tests.

In the test class, we inject the factory into the constructor. With the factory, we can create a HttpClient which is used in the tests to make HTTP requests.


