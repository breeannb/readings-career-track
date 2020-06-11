# Class 09 Reading 

## [mongoose instance methods](https://mongoosejs.com/docs/guide.html#methods)
- [Quickstart Guide](https://mongoosejs.com/docs/index.html)
- If you want to add additional keys later, use the Schema#add method.
- Keys may also be assigned nested objects containing further key/type definitions like the meta property above. This will happen whenever a key's value is a POJO that lacks a bona-fide type property. In these cases, only the leaves in a tree are given actual paths in the schema (like meta.votes and meta.favs above), and the branches do not have actual paths.
- When you create a new document with the automatically added _id property, Mongoose creates a new _id of type ObjectId to your document.
- You can also overwrite Mongoose's default _id with your own _id. Just be careful: Mongoose will refuse to save a document that doesn't have an _id, so you're responsible for setting _id if you define your own _id path.
- Instance methods - Instances of Models are documents. Documents have many of their own built-in instance methods. We may also define our own custom document instance methods.
- Now all of our animal instances have a findSimilarTypes method available to them.

## [mongoose static methods](https://mongoosejs.com/docs/guide.html#statics)
- Statics - You can also add static functions to your model. There are two equivalent ways to add a static:
    - Add a function property to schema.statics
    - Call the Schema#static() function
- Do not declare statics using ES6 arrow functions (=>). Arrow functions explicitly prevent binding this, so the above examples will not work because of the value of this.

## [mongoose middleware](https://mongoosejs.com/docs/middleware.html)
- Types of middleware: 
    - document middleware, model middleware, aggregate middleware, and query middleware.
- Middleware document functions: 
    - validate
    - save
    - remove
    - updateOne
    - deleteOne
    - init (note: init hooks are synchronous)
- Query middleware is supported for the following Model and Query functions. In query middleware functions, this refers to the query.
    - count
    - deleteMany
    - deleteOne
    - find
    - findOne
    - findOneAndDelete
    - findOneAndRemove
    - findOneAndUpdate
    - remove
    - update
    - updateOne
    - updateMany
- Aggregate middleware is for MyModel.aggregate(). Aggregate middleware executes when you call exec() on an aggregate object. In aggregate middleware, this refers to the aggregation object.
    - aggregate 
- Model middleware is supported for the following model functions. In model middleware functions, this refers to the model.
    - insertMany
- All middleware types support pre and post hooks. How pre and post hooks work is described in more detail below.
    - Note: If you specify schema.pre('remove'), Mongoose will register this middleware for doc.remove() by default. If you want to your middleware to run on Query.remove() use schema.pre('remove', { query: true, document: false }, fn).
    - Note: Unlike schema.pre('remove'), Mongoose registers updateOne and deleteOne middleware on Query#updateOne() and Query#deleteOne() by default. This means that both doc.updateOne() and Model.updateOne() trigger updateOne hooks, but this refers to a query, not a document. To register updateOne or deleteOne middleware as document middleware, use schema.pre('updateOne', { document: true, query: false }).
    - Note: The create() function fires save() hooks.
