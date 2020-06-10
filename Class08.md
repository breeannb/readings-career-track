# Class 08 Mongoose 

## [mongoose populate](https://mongoosejs.com/docs/populate.html)
- MongoDB has the join-like $lookup aggregation operator in versions >= 3.2. Mongoose has a more powerful alternative called populate(), which lets you reference documents in other collections.
- Population is the process of automatically replacing the specified paths in the document with document(s) from other collection(s). We may populate a single document, multiple documents, a plain object, multiple plain objects, or all objects returned from a query.
- Saving refs
    - Saving refs to other documents works the same way you normally save properties, just assign the _id value
- Population
    - So far we haven't done anything much different. We've merely created a Person and a Story. Now let's take a look at populating our story's author using the query builder
    - Populated paths are no longer set to their original _id , their value is replaced with the mongoose document returned from the database by performing a separate query before returning the results.
    - Arrays of refs work the same way. Just call the populate method on the query and an array of documents will be returned in place of the original _ids.
- Setting Populated Fields
    - You can manually populate a property by setting it to a document. The document must be an instance of the model your ref property refers to.
- Checking Whether a Field is Populated
    - You can call the populated() function to check whether a field is populated. If populated() returns a truthy value, you can assume the field is populated.
    - A common reason for checking whether a path is populated is getting the author id. However, for your convenience, Mongoose adds a _id getter to ObjectId instances so you can use story.author._id regardless of whether author is populated.
- What If There's No Foreign Document?
    - Mongoose populate doesn't behave like conventional SQL joins. When there's no document, story.author will be null. This is analogous to a left join in SQL.
    - If you have an array of authors in your storySchema, populate() will give you an empty array instead.
- Field Selection
    - What if we only want a few specific fields returned for the populated documents? This can be accomplished by passing the usual field name syntax as the second argument to the populate method
- Populating Multiple Paths
    - If you call populate() multiple times with the same path, only the last one will take effect.
- Query conditions and other options
    - What if we wanted to populate our fans array based on their age and select just their names?
- Populating multiple existing documents
    - If we have one or many mongoose documents or even plain objects (like mapReduce output), we may populate them using the Model.populate() method. This is what Document#populate() and Query#populate() use to populate documents.
- Populating across multiple levels
    - Populate lets you get a list of a user's friends, but what if you also wanted a user's friends of friends? Specify the populate option to tell mongoose to populate the friends array of all the user's friends
- Cross Database Populate
    - Let's say you have a schema representing events, and a schema representing conversations. Each event has a corresponding conversation thread.


## [express routing](https://scotch.io/tutorials/learn-to-use-the-new-router-in-expressjs-4)
- Express 4.0 comes with the new Router. Router is like a mini express application. It doesn't bring in views or settings, but provides us with the routing APIs like .use, .get, .param, and route.
- Application Structure
    - package.json  // set up our node packages
    - server.js     // set up our app and build routes
- Starting Our Application
    - ```{```
    ```"name": "express-router-experiments",```
    ```"main": "server.js",```
    ```"dependencies": {```
        ```"express": "~4.0.0"```
    ```}```
```}```
- Creating Our Server
    - We will use Express to start our application server. Since we defined server.js as the main file in package.json, that is the file that Node will use.
- Express Router
    - What exactly is the Express Router? It is a mini express application without all the bells and whistles of an express application, just the routing stuff. Let's take a look at exactly what this means. We'll go through each section of our site and use different features of the Router.
- Basic Routes express.Router()
- Route Middleware router.use()
- Route with Parameters /hello/:name
- Route Middleware for Parameters
- Login Routes app.route
- Conclusion
    - Use express.Router() multiple times to define groups of routes
    - Apply the express.Router() to a section of our site using app.use()
    - Use route middleware to process requests
    - Use route middleware to validate parameters using .param()
    - Use app.route() as a shortcut to the Router to define multiple requests on a route

## [mongoose virtuals](https://mongoosejs.com/docs/populate.html#populate-virtuals)
- So far you've only populated based on the _id field. However, that's sometimes not the right choice. In particular, arrays that grow without bound are a MongoDB anti-pattern. Using mongoose virtuals, you can define more sophisticated relationships between documents.
- You can also use the populate match option to add an additional filter to the populate() query. This is useful if you need to split up populate() data:
- Populate Virtuals: The Count Option
- Populate virtuals also support counting the number of documents with matching foreignField as opposed to the documents themselves. Set the count option on your virtual
- Populate in Middleware
- You can populate in either pre or post hooks. If you want to always populate a certain field, check out the mongoose-autopopulate plugin.
