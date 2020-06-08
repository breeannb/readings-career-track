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

# Notes from Class 
- Difference between a client and a server
    - Server is usually a cloud-based server 
        - provides a service and allows clients to connect 
        - Server is usually Express 
            - can see import statements (esn)
            - Node can use this if we want it to, but esn is newer 
    - Client runs within a browser 
        - have little control on what clients connect to our server 
        - Client side code is usually React 
            - common.js require module imports syntax for react 
- HTTP (Hypertext Transfer Protocol ) - an application protocol (rules ) used to send info across the web or computers. 
    - Standard flow: 
        - a client creates a connection to the server 
        - the client sends a request to the server 
    - Http is only text based
        - requqest and response is sent as plain text 
        - GET / HTTP/ 1.1 (Get is the method / is the path http, and then version is all sent to the server )
            - Host: example.com 
            - Accept-Language: us-en 
                - the above two are headers 
        - then http tells the server what text based package it can send 
            - in the example, shows 'HTTP/1.1 200 OK' will display status code and status message 
                - also called status code 
                - then followed by header information 
                - a blank line to show that we are done with the headers 
                    - examples content-type: text/html
                        - then body of the response 
        - then you close the connection 
- When a client sends a message to the server: 
    - sends the method, path, HTTP and version 
    - can ahve a POST request as well 
        - in this case, we would also have a blank line after headers and then the body 

- HTTP Response 
    - again, status code and status message, Ryan has in notes commong messages 

- In Javascript Applications, we have a stack 
    - at the top, we have express (express is built on top of a node library called http.  http library is built upon net library(another node libary) )
        - express is kind of a phone operator that routes to the correct line
        - express is basically a router 
            - app.get ('./dogs', () => {})
                - get is the method
                - ./dogs is the path 
                - () => {} is handler function 
            - expresses job is for a particular request and method, this is your response 
    - http's job is to take the text packets and turn into a javascript object 
        - it takesthe GET, headers and body and turns it into something like this:  
            - { method: 'GET
                path: './dogs, 
                headers: {}, {}, 
                body}
            - why? It is easier to deal with javascript object than with a string 
            - it will do the same thing for response, but for object to text 
            - so job is to construct requests and responses 
    - net libary establishes connections for us 
        - allows clients to connect to our server 
        - built on top of tcp, which tells us how connections are established or made to begin with 

Model of a Request Cycle 
 
Client wants to get a request to hit all dogs in our database. to do this, they need to hit the /dog path and GET 
    - in Ryan's example, they did localhost/dogs
        - this automatically creates a get request 
        - this makes a request and inside the request packet
            - method, path, http 1.1, header info, body info 
            - GET /dogs HTTP 1.1 
                - []
    - express is built on top of the http library and net library 
    - takes text and parses the request 
        - object then is passed in express library 
        - when we do (req, res)
            - req is the request that http parses for us and goes to express
            - then request will route to the appropriate handler to run, such as the ones below
                - app.get('./dogs', (req, res) => {})
                - app.get('./cats', (req, res) => {})
            - the above, we will choose the dog path to get all dogs 
        - res.send() will trigger to send the response, this will be send to http, then http response packets will receive that
            - response packets text based
            - then is sent back to the server 

TCP is another protocol 
    - establishes connection between clients and servers 
    - before we start, client has to connect to server 
        - always done the same way, three part handshake 
            - client will send message to server, is the server even there? 
            - server then responds to client saying 'it is there'
            - client is responsible for sending one last message acknowledging it got the message 
        - after those steps happen, we officially have a connection between client and server with a duplex server 
            - duplex server says that messages can be sent through 'a pipe' in both directions 
        - we have syn, syn-ach and ach calls  
            - syn(ring)
            - syn-ach(hello)
            - syn-ach(hi)
        - after that is done, we kill the connection


Establishing a Port on a TCP 
    - again, does the 3 part handshake, after it is established, we create pipe between a message and a server, making it a duplex stream 

In Node, there is a library called net 
    const net = reqire('net'); 

    //established connection 
    //once client connects,
    const server = net.createServer((client) => { 
        console.log('Client connected!!'); 
        //ryan opened a browser for the local host 7890, so everytime we placed the localhost and refereshed, we get client connected in the terminal console.logged
    }); 

    //port to listen for clients to connect. If a client tries to connect, this callback function is what gets invoked
    // then send the request to us 
    server.listen(7890, () => {
        console.log('Listening on 7890);
    });

    run this on node server.js in the terminal 
    npm run start:watch to see it as ryan changes code 

So now the above, the handshake has been updated 
    - the below is a nevent listener, which is placed in the const server 
    - we are listening to the data event, waiting for the client to access the server 
    client.on('data', data => {
        console.log(data); 
    }); 
        - browser will send from client to server (request)
        - in order for the server to listen for client, we need an event listener 
        - since are building this on top of tcp, which is what lets messages go back and forth 
        - it will send us back at this point of just data, the string of a buffer, binary representation of the string
            - each number in this represents a single letter (ryan was showing utf strings and their corresponding letters )
            - the example shown was the http GET 
            - you can convert it to a string by placing toString() at the end to get the message, which is the http request 

Now we want to respond, inside the client.on 
    client.end(`hello`);//send whatever text we have in here back to the response and closes the connection
        - if we do just the above, it comes back blank, we need to send a response to the client 
        - so we need to construct an http response 
    - so we type client.end(`HTTP/1.1 200 OK
        //put header information here
        Date: Mon, 08 June 2020 18:19 GMT
        Content-Length: 5 
        Content-Type: text/plain  //can also send object application/json
        
        hello`); //hello is the body in this case 
        - if we wnat it to be html, it would need to be text/html and establish the number of characters 
        - can also have the body = '<1> hellow </h1> and od the body,. length as body.length 

Now ryan put in the browser /dogs path.  Right now, it is sending only hello 
    - what if we wanted to send json instead 
