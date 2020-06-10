# Class 07 Reading: Express

## Express Routing 
- Event driven system
    - ```app.get('/thing', (req,res) => {})```
    - This is the same pattern we see in Vanilla JS, jQuery
    - ‘When a get event happens in our server, on “/thing”, run this function…’
- Request Object 
    - (req,..)
    - /:parameters
        - app.get('/api/:thing',...) = req.params.thing
    - Query Strings
        - http://server/route?ball=round = req.query.ball
- Response Object
    - (..., res)
    - Responsible for sending data back to the browser
    - Has methods like send() and status() that Express uses to format the output to the browser properly
        - Sends Headers
            - Cookies
            - Status Codes

## Express Middleware 
- What does it do?
    - A series of functions that the request “goes through”
    - Each function receives request, response and next as parameters
    - Types of middleware: Application and Route
    - Application Middleware
        - Error Handling
        - Bringing in other routes
        - Applies Defaults
        - JSON, Body and Form Parsing
        - Runs on every request
    - Route Middleware
        - Dealing with specific things for a route
        - Generally, things many routes would participate in
            - Are you logged in?
            - What is your IP?
            - Have we seen you here before?
- How can we take advantage?
    - Logging
    - Dynamic Model Loading
    - Browser, Location, User specific content
    - Consistent Data Transition/Modeling/Preparation (Pre-Render)

## Modularization & Seperation Concerns 
- Modularizing your code into logical chunks
- Each thing should do the thing its best at
- Dan Abramov: http://react-file-structure.surge.sh/
    - "just move it around until it feels right' 

## CRUD Operations with REST and Express 
- CREATE
    - ```app.post('/resource')```
- READ
    - ```app.get('/resource')```
- UPDATE
    - ```app.put('/resource/:id')```
- DESTROY
    - ```app.get('/resource/:id')```

## Server Testing 
- Generally, avoid starting the actual server for testing
- Instead, export your server as a module in a library
- Then, you can use supertest to run your tests
    - This will hit your routes as though your server was running, without actually starting it
    - That’s one less thing to go wrong (eliminate variables when testing!)
- Additionally, you can wrap superagent in a module (the demo code created an agent.js module that does this)
    - Doing this, allows you set up a “mock” of this new agent module
    - Create a folder called __mocks__ where the agent.js file is with an agent.js file in it
    - When you invoke jest.mock() on the agent file in your test, jest is smart enough to use that mocks version instead of the real one
    - Why is this cool? We can 100% fake every call to the API. Again – you don’t want your tests of the web server to be dependent on the API running, so mock (fake) it, so that you are testing only the interface to the API, not the actual data
    - You test the data/veracity of the API when you write your API tests, not web server tests…    

## Test Pyramid 
- Server Testing crosses boundaries
    - Units: Server Internal Functions
        - Mock any integrations (like data fetching)
    - Integration: How it connects to other services
       -Really connect to other services (hard dependencies)
    - Acceptance
        - The server might be a dependency of some other test

## Additional Resources from Readings
### Videos 
- [express middleware explained](https://www.youtube.com/watch?v=9HOem0amlyg)
    - really appreciate this video for the visual interpretations :) 
    - isAuthenticated() will pass to uploads 
    - next() parameter - all middleware carries this, which is needed for passing along request to next function in chain
    - controller.upload - last function in the chain 
    - in this example, they made a new file and copied app.js file 
        - app.use(body.parser())
        - app.get

### Bookmark/Skim 
- [using express middleware](https://expressjs.com/en/guide/using-middleware.html)
- [express middleware](https://www.tutorialspoint.com/expressjs/expressjs_middleware.htm)
- [using express routing;](https://expressjs.com/en/guide/routing.html)
- [supertest](https://github.com/visionmedia/supertest)
- [express middleware list](https://expressjs.com/en/resources/middleware.html)
- [http status codes](https://www.restapitutorial.com/httpstatuscodes.html)

# Class Notes: 

## Continueing with Express 

- Test Pyramid 
    - Unit Test 
        - Server Internal Functions 
        - Mock any integrations like data fetching 
        - Testing of a function, calling a function and making sure it returns that data 
    - Integration 
        - How it connects to other services 
            - really connect to other services(hard dependencies)
            - test integrations are connecting 
    - Acceptance 
        - the server might be a dependancy of some other test 

- Express Pathing 
    - can add params, anything with : in front creates a param 
    - params can be anywhere in the url
    - can have multiple params
    
- Express Router 
    - every resource will have its own router file

- Express Response Methods 
    - res.end - end the response with text 
        - similar to socket.end('') - takes a string and ends a response 
    - res.json - take an object and json.stringify for us, the end the response and send json 
    - res.send - end the response and automaticlaly figure out the type 
        - can send res.send('text') sees it is text 

- app.use(express.json())
    - parse the incoming request data as JSON 


- Express Middleware 
    - just a function that is invoked between incoming request and outgoing response 
    - cors, json body parser (express.json()) are two that we already used 
        - cors added headers 
        - express.json parsed req body 
    - all of this happened before we got to our handler app.get('/', handler )
    - ``` const myMiddleware = (req, res, next) => {};```
        - next in this case allows us to go to the next piece of middleware 

- to use middleware
    - app.use(myMiddleware); 

- apply middleware to a specific path and to a specific route
- if middleware never sends it is the response was probably errored 
    - express was waiting for the last middleware to end 

- Error Middleware 
    - always the last middlware that you express application needs 
        - signature: ``` module.exports = (err, req, res, next) => {}; ```
    - will hit whenever one of your routes throws an error.

## Demo Code 
    - In terminal: npm init @alchemycodelab 

    - in Server.js 
    - in connect.js - actual connection to mongodb 
        - ongoose.connection - helps console log things for us 
        - mongoose.connection.on('disconnected) - console logs 
        - mongoose.connection('error') - console.logs error 
        - return mongoose.connect(url, {
            a list of configuration things 
        })
    - in app.js 
        - not found middleware and error middleware 
        - app.use('api/v1/RESOURCE) - this will be changed to our routes 
    - server.js 
        - has our listener 
    - services folder 
        - calls any external 3rd party apis 
    - models folder 
        - mongoose models 
    - routes folder
        - routes files 
    - rename env-example to .env file 
        MONGODB_URI=mongodb://localhost:27017/demo

- Writing some middleware 
    - in app.js Ryan wrote a simple route
        - ```app.get('/', (req, res) => {
            res.end('hello');
        });```
            - this will show on the page the word hellow 
    - app.use((req, res, next) => {
        console.log('i am middleware');
        next();
    });
        - this middleware will trigger before the route will
    - in between app.use(express.json()) and the app.get it will rspond 

- enum: string can only be one of these strings 

- models are always capitalized and singular for files etc 
- pizzas.js is always pluralized 
