# Class 13 Mongo Aggregations 

## [Mongo Aggregations](https://docs.mongodb.com/manual/core/aggregation-pipeline/)
- Aggregation Pipeline
    - The aggregation pipeline is a framework for data aggregation modeled on the concept of data processing pipelines.
    - Documents enter a multi-stage pipeline that transforms the documents into aggregated results.
    - The MongoDB aggregation pipeline consists of stages. Each stage transforms the documents as they pass through the pipeline. Pipeline stages do not need to produce one output document for every input document; e.g., some stages may generate new documents or filter out documents.
    - Pipeline stages can appear multiple times in the pipeline with the exception of $out, $merge, and $geoNear stages. For a list of all available stages, see Aggregation Pipeline Stages.
    - MongoDB provides the db.collection.aggregate() method in the mongo shell and the aggregate command to run the aggregation pipeline.
- Pipeline Expressions
    - Some pipeline stages take a pipeline expression as the operand. Pipeline expressions specify the transformation to apply to the input documents. Expressions have a document structure and can contain other expression.
    - Pipeline expressions can only operate on the current document in the pipeline and cannot refer to data from other documents: expression operations provide in-memory transformation of documents.
    - Generally, expressions are stateless and are only evaluated when seen by the aggregation process with one exception: accumulator expressions.
    - The accumulators, used in the $group stage, maintain their state (e.g. totals, maximums, minimums, and related data) as documents progress through the pipeline.
    - Changed in version 3.2: Some accumulators are available in the $project stage; however, when used in the $project stage, the accumulators do not maintain their state across documents
- Aggregation Pipeline Behaviour 
    - In MongoDB, the aggregate command operates on a single collection, logically passing the entire collection into the aggregation pipeline. To optimize the operation, wherever possible, use the following strategies to avoid scanning the entire collection.
    - Pipeline Operators and Indexes
        - $match
            - The $match stage can use an index to filter documents if it occurs at the beginning of a pipeline.
        - $sort
            - The $sort stage can use an index as long as it is not preceded by a $project, $unwind, or $group stage.
        - $group
            - The $group stage can sometimes use an index to find the first document in each group if all of the following criteria are met:
                - The $group stage is preceded by a $sort stage that sorts the field to group by,
                - There is an index on the grouped field which matches the sort order and
                - The only accumulator used in the $group stage is $first.

        - $geoNear
            - The $geoNear pipeline operator takes advantage of a geospatial index. When using $geoNear, the $geoNear pipeline operation must appear as the first stage in an aggregation pipeline.

## [Aggregations by Example](https://www.compose.com/articles/aggregations-in-mongodb-by-example/)

- Starting an Aggregation Pipeline
    - Aggregations are a set of functions that allow you to manipulate the data being returned from a MongoDB query, and in this article, we'll explore MongoDB aggregations by demonstrating a few.
    - In particular, we'll take a look at how to create basic data transformations using aggregations, and then explore how to create more complex queries by chaining multiple transformations together.
- Getting an aggregation pipeline started is a simple affair: simply call the aggregate function on any collection.
- The aggregate function accepts an array of data transformations which are applied to the data in the order they're defined. This makes aggregation a lot like other data flow pipelines: the transformations that are defined first will be executed first and the result will be used by the next transformation in the sequence.
-  The order in which you perform transformations can make a big difference since you'll want to filter out any collections you don't want to manipulate before you do any complex or intensive operations on them.
- Matching Documents
    - The first stage of the pipeline is matching, and that allows us to filter out documents so that we're only manipulating the documents we care about. The matching expression looks and acts much like the MongoDB find function or a SQL WHERE clause.
    - This will return the array of customers that live in the 90210 zip code. Using the match stage in this way is no different from using the find method on a collection.
- Grouping Documents
    - Once we've filtered out the documents we don't want, we can start grouping together the ones that we do into useful subsets. We can also use groups to perform operations across a common field in all documents, such as calculating the sum of a set of transactions and counting documents.
    - The $group transformation allows us to group documents together and performs transformations or operations across all of those grouped documents. In this case, we're creating a new field in the results called count which adds 1 to a running sum for every document. The _id field is required for grouping and would normally contain fields from each document that we'd like to preserve (ie: phoneNumber). Since we're just looking for the count of every document, we can make it null here.
    - Here we saw the use of the $sum arithmetic operator, which sums a field in all of the documents in a collection. We can group our documents together on any fields we'd like and perform other types of computations as well. Let's take a look at some of the other operators we can use and how we can use them.
- Gaining Insights with Sum, Min, Max, and Avg
    - Transactions are a great place to stretch our proverbial legs when it comes to mathematical operations. Let's analyze our transactions and see if we can gain some insights into our product catalog.
    - The $gte and $lt operators are comparators that allow us to limit our dates to specific range. In our case, we want the transactionDate to be greater than or equal to the first day in January and less than the first day in February. Notice also that we're using Zulu (UTC) time here; you'll want to make sure your transactions are inserted in the proper timezone for this to work, but for this example we'll assume that all timezones are input in Zulu time.
    - Some other helpful monthly metrics we might want are the average price of each transaction, and the minimum and maximum transaction in the month.
    - we could even take this a step further by calculating the standard deviation across all transactions using stdDevPop or modify our groupings to exclude outliers by changing our $match conditions.
- Wrapping Up
    - Now that we know how to use the aggregations pipeline we can start to combine groups, operations, and even other matching parameters to gain deep and detailed insights into any business. While there are plenty of other operations we can perform that weren't covered in this article, it should provide a good launching point for anyone interesting in analyzing data stored in MongoDB.
