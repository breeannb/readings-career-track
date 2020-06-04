# Class 06 - HTTP and REST 

## [HTTP](https://tools.ietf.org/html/rfc7231)
- The Hyper Text Transfer Protocol (HTTP) is a stateless request-response application layer protocol and the world wide web's foundation.
- Apps using HTTP subscript to client-server computing model 
- The HTTP specification defines how requests and responses should be formatted, but not what a service should represent.
- HTTP is often associated with serving .html files but is also used to transfer images, videos, .json, .xml, binary executables, and much more.

# HTTP Requests 
- A HTTP/1.1 request is formatted in text and transferred using TCP.
- The first line of the request contains the METHOD, URL, and HTTP VERSION. The following lines are the request HEADERS.
- Headers containing more than one value separate each value using a semicolon. The header section of the request is terminated with an empty line. An optional body follows the header section.
- Example HTTP Request: 
    > POST /api/note HTTP/1.1 
    > Host: api.example.com
    > Origin: www.example.com
    > Authorization: Bearer bHVsIHRoaXMgaXMgYSBmYWtlIHNlY3JldCB0b2tlbg==
    > Accept: application/json
    > Content-Type: application/json; charset=UTF-8
    > Content-Length: 58

    >  {"title":"kata","content":"get 100 points on hacker rank"}  

# HTTP Response 
- A HTTP/1.1 response is also formatted in text and transferred using TCP. 
- The first line of the response contains the HTTP VERSION, STATUS CODE, and STATUS MESSAGE
-  The following lines are the request headers and are formatted exactly the same way as the request headers. The header section of the request is terminated with an empty line. An optional body follows the header section.
- Example HTTP Response: 
    > HTTP/1.1 200 OK
    > Date: Tue, 22 Aug 2017 06:34:16 GMT
    > Content-Type: application/json; charset=UTF-8
    > Content-Encoding: UTF-8
    > Content-Length: 82
    > Last-Modified: Mon, 21 Aug 2017 12:10:38 GMT
    > Server: Apache/1.3.3.7 (Unix) (Red-Hat/Linux)
    > ETag: "3f80f-1b6-3e1cb03b"
    > Connection: close

    > {"id":"1234123412341324","title":"kata","content":"get 100 points on hacker rank"}


## REST 
- REST is acronym for REpresentational State Transfer. In layman’s terms, is a means by which we can reference, manipulate, and transfer state
- uses a common set of methods (called “verbs”) to operate on the state of a resource (“noun”), generally using HTTP as the transfer protocol.
- A “RESTful Endpoint” is a URI that identifies the resource. When addressed with a proper method, you are able to effect state. In normal terms, this means “Performing CRUD operations over HTTP”
- Generally speaking, RESTful endpoints deliver data in JSON format. The best practice is to supply a header with metadata and a collection of results

## REST Documentation (Swagger)
- The standard for documenting REST APIs is with a “live” documentation system: Open API (formerly “Swagger”)
- Once generated, Swagger Docs present developers a way not only see how to use an API, but to actually use it. Yes, this is documentation that allows for live requests from with it.
- Example: [Star Wars API](https://app.swaggerhub.com/apis/ahardia/swapi/1.0.0#/)

## How to Generate Your Own Swagger Documentation 
- Visit and review the docs and overview at Swagger.io
- Sign in to the Swagger Inspector
- Visit your API, using all applicable REST endpoints and data
- Note that on the right side, it’ll keep your history
- Once you’ve gone through all of your routes, use the radio buttons select the routes you want to document
- Click the “Create API Definition” button
- Follow the instructions to import your new API documentation to Swagger Hub
- You can leave it running there, or download the definition as .yml or .json and use it in your own project

## ADDITIONAL RESOURCES 
### Videos 
- [http and rest](https://www.youtube.com/watch?v=Q-BpqyOT3a8)

### Bookmark/Skim 
- [http basics](https://code.tutsplus.com/tutorials/http-the-protocol-every-web-developer-must-know-part-1--net-31177)
- [what is REST](https://restfulapi.net/)
- [swagger documentation](https://swagger.io/docs/)
- [swagger editor](https://editor.swagger.io/)
- [http reference](https://code-maze.com/the-http-reference/)
- [rest reference](https://www.restapitutorial.com/lessons/httpmethods.html)
