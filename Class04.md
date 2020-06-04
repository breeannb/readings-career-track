# Class 03 Reading 

## Reading Questions 
1. Why would a developer choose to make data models?
    - data models allow ease of access and integrity of data, making it easier for an individual to access and retain 

2. What purpose do CRUD operations serve?
    - to provice a memorable frameowok to remind developers on how to create a full, useable application 

3. What kind of database is Postgres? What kind of database is MongoDB?
    - Postgres is object-relational and MongoDB is a NoSQL Database Program 

4. What is Mongoose and why do we need it?
    - is an object Data Modeling library for MongoDB and Node.js.  It manages relationships with data, provides schema validation and is used to translate between objects in code and the representation of those objects in MongoDB. 

5. Describe how NoSQL Dtabases scale horizontally
    - essentially, NoSQL databases can handle traffic, as they have more smaller servers added to the database.  

6. Give one strong argument for and against NoSQL Databases
    - for: more suitably priced 
    - against: difficult joins and complex queries 

7. Define three related pieces of data in a possible application. An example for a store application might be Product, Category and Department. Describe the constraints and rules on each piece of data and how you would relate these pieces to each other. For example, each Product has a Category and belongs in a Department.
    - Photography Site: Photo -> Type of Photo (Landscape, Portrait, Nature, etc) -> Gallery
    - Each Photo has a Type, and each Type will present in a gallery 

8. Name 3 cloud based NoSQL Databases
    - Redis, Amazon, MongoDB

## Vocab Terms 
- **database** - provides file creation, data entry, update, query and reporting functions.
- **data model** - define how the logical structure of a database is modeled
- **CRUD** - Create, Read, Update, and Delete - are the four basic functions that models should be able to do, at most.
- **schema** - The database schema of a database is its structure described in a formal language supported by the database management system (DBMS).
- **sanitize** - the process of deliberately, permanently and irreversibly removing or destroying the data stored on a memory device to make it unrecoverable.
- **Structured Query Language (SQL)** - Structured Query Language (SQL) is a programming language that is typically used in relational database or data stream management systems.
- **Non SQL (NoSQL)** - NoSQL is a non-relational database that stores and accesses data using key-values.
- **MongoDB** - MongoDB is a cross-platform and open-source document-oriented database, a kind of NoSQL database.
- **Mongoose** - Mongoose is an Object Data Modeling (ODM) library for MongoDB and Node.js.
- **record** - A record is composed of fields and contains all the data about one particular person, company, or item in a database.
- **document** - A document database is a type of nonrelational database that is designed to store and query data as JSON-like documents.
- **Object Relation Mapping (ORM)** - Object-relational mapping (ORM, O/RM, and O/R mapping tool) in computer science is a programming technique for converting data between incompatible type systems using object-oriented programming languages. 

## Resources 
Kept it simple and used medium.com/ google and w3 mostly as well as readings below

## Additional Resources from Assignment (To keep Links for reference)
- [In Memory Database Testing](https://dev.to/paulasantamaria/testing-node-js-mongoose-with-an-in-memory-database-32np)
- [The Repository Design Pattern](https://cubettech.com/resources/blog/introduction-to-repository-design-pattern/)
- [mongo memory server](https://www.npmjs.com/package/mongodb-memory-server)

# In Class 04 Notes 
To solve our problems in this way: 
    - Input
        - need to parse, so parse with type and payload 
        - is it good? We wrote a valid function 
    - Execute 
        - we want to create 
        - to find
        - then to delete a note 
    - Output 
        - display a note 
        - display a list of notes 

Input.js
    Things to consider right away for Input.js: 
        - export 
        - There are two functions, we started with valid: 
            - 
    Things to consider for test: 
        - import input 
        - then describe input 
            - valid test 

npm i -D mongodb-memory-server 
    - lets us start mongodb in our tests: 
        - const mongoose = require('mongoose');
        - const { MongoMemoryServer } from ('mongodb-memory-server'); 
    - before starting tests, need to start mongo db 
        - need to establish after describe
            - const mongodb = new MongoMemoryServer(); 
    - .lean takes from javascript documentation to json 
        - cannot call .lean on .create at all 

Output
    - in index.js we need to bring in mongoose 
        - const mongoose = require('mongoose');
        - mongoose.connect('mongodb://localhost/:27017/notes', {
            usenew
        })

    - bring 


    node index.js --add "my note" wil lallow us to see in mongodb connect our notes, addes 


Another project: 
    In the terminal: 
        - npm i express mongoose cors nodemon 
        - npm i -D supertest 
        npm i 
    lib folder
        - app.js 
            -   import express and app 
            - export our app 
    server.js 
        - import app 
        - listen on any hardcoded port 
        - import mongoose 
        - then connect to mongodb with mongoose on localhost/shareable  
        - 
    - then npm run start:watch to start on the port 
    - make a test file __test__
        - then app.test.js 
            - this is an integration test 


