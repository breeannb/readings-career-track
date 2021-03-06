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
5. Define three related pieces of data in a possible application. An example for a store application might be Product, Category and Department. Describe the constraints and rules on each piece of data and how you would relate these pieces to each other. For example, each Product has a Category and belongs in a Department.
    - 

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

### Cloud Databases 
- [MLab](https://www.mlab.com/) - remotely hosted mongoDB systems. Easily setup a free database (or pay for more horsepower). Works great with Heroku
- [Atlas](https://www.mongodb.com/cloud/atlas) - Cloud based, highly scalable Mongo DB
- [DynamoDB](https://aws.amazon.com/dynamodb/) - AWS NoSQL Database. Very highly scalable. Also provides a ‘mongoose’-like ORM called ‘dynamoose’
- [CosmosD](https://cosmos.azure.com/) - The Microsoft Azure equivalent for Atlas and Dynamo

### Videos 
- [sql vs nosql](https://www.youtube.com/watch?v=ZS_kXvOeQ5Y)

### Bookmark/Skim 
- [nosql vs sql](https://www.thegeekstuff.com/2014/01/sql-vs-nosql-db/?utm_source=tuicool)
- [nosql modeling techniques](https://highlyscalable.wordpress.com/2012/03/01/nosql-data-modeling-techniques/)
- [mongoose api](https://mongoosejs.com/docs/api.html#Model)

# In Class Notes 

## SQL Database 
- Ryan created a table called Dogs 
- Dogs has an id that has a primary key, name age and weight 
    - inserted into the dogs, name, age and weight and gave values 
    - once inserted, should be able to select and see the dog that is created 
    - Database is stored in a place called 1687 (shows in Postgres at the bottom )
    - Ryan showed that on the pc terminal, the cd 16387  16387 you can find the file name in the terminal stored 
- In the terminal: 
    - npm i mongoose 
    - in lib directory, create another directory called 'models'
    - then Ryan made Dog.js which is equivalent to our dog table.  
        - should be uppercase and singular 
        - inside of the file 
            - import mongoose 
                - const mongoose = require('mongoose');
                - const schema = new mongoose.Schema({
                    name: { 
                        type: String, (type of data)
                        required: true (is it required?)
                    },
                    age: { 
                        type: Number, 
                        required: true 
                    }, 
                    weight: {
                        type: String
                    }

                });
            - after making schema export: 
                - module.exports = mongoose.model('Dog', schema);