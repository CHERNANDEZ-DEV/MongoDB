# What is MongoDB?

MongoDB is a document database. It stores in a type of JSON format called BSON.

A record in MongoDB is a document, wich is a data structure composed of key value pairs similar to the structure of JSON objects. 

This does not mean that relational data cannot be stored in document databases. It means that relational data is stored differently. A better way to refer to it is as a non tabular database.

You can still have multiple group of data too. In MongoDB, instead of tables these are called collections.

## MongoDB QUERY API

The MongoDB QUERY API is the way you will interact with your data.

The MongoDB Query API can be used two ways:

* CRUD operations
* Aggregation Pipelines

You can use the MongoDB Query API to perform: 

* Adhoc queries with **mongosh**, Compass, VS Code, or a MongoDB driver for the programming language you use.
* Data transformations using aggregation pipelines.
* Document join support to combine data from different collections.
* Graph and geospatial queries.
* Full-text search.
* Indexing to improve MongoDB query performance. 
* Time series analysis.

## MongoDB Shell (mongosh)

Is a fully functional JavaScript and Node.js 16.x REPL environment for interacting with MongoDB deployments. You can use the MongoDB Shell to test queries and operations directly with your database. 

## MongoDB architecture

![MongoDB architecture](https://images.idgesg.net/images/article/2021/06/document-store-100893897-large.jpg?auto=webp&quality=85,70 "mongoDB architecture")


### Show all databases

```
show dbs
```

### Change or Create a Database

```
use <name_database>
```

**Remember:** In MongoDB, a database is not actually created until it gets content!

### Create collections

There are two ways to create a collection

**First Method:** You can create a collection using the **createCollection()** database method.

```
db.createCollection("posts")
```

**Second Method:** You can also create a collection during the **insert** process.

```
db.posts.insertOne(object)
```
This will create the "posts" collection if it does not already exist.

### Insert Documents

There are methods to insert documents into a MongoDB database.

**insertOne()**

To insert a single document. This method inserts a single object into the database.

```JSON
db.posts.insertOne({
  title: "Post Title 1",
  body: "Body of post.",
  category: "News",
  likes: 1,
  tags: ["news", "events"],
  date: Date()
})
```

**InsertMany()**

To insert multiple documents at once, this method inserts an array of objects into the database. 

```JSON
db.posts.insertMany([  
  {
    title: "Post Title 2",
    body: "Body of post.",
    category: "Event",
    likes: 2,
    tags: ["news", "events"],
    date: Date()
  },
  {
    title: "Post Title 3",
    body: "Body of post.",
    category: "Technology",
    likes: 3,
    tags: ["news", "events"],
    date: Date()
  },
  {
    title: "Post Title 4",
    body: "Body of post.",
    category: "Event",
    likes: 4,
    tags: ["news", "events"],
    date: Date()
  }
])
```

### Find Data

There are 2 methods to find and select data from a MongoDB collection, **find()** and **findOne()**

**find()** to select data from a collection in MongoDB, this method accepts a query object, if left empty, all documents will be returned. 

```JSON
db.posts.find()
```
**findOne()** to select only one document, we can use the **findOne()** method, this method accepts a query object, if left empty, it will return the first document it finds.

```JSON
db.posts.findOne()
```

**Note:** This method only returns the first match it finds. 

### Querying Data

To query, or filter, data we can include a query in our **find()** or **findOne()** methods.

```JSON
db.posts.find( {category: "News"} )
```

### Projection

Both find methods accept a second parameter called **projection**.
This parameter is an object that describes which fields to include in the results. 

```JSON
db.posts.find({}, {title: 1, date: 1})
```

**Note:** The **id** field is also included. This field is always included unless specifically excluded.

We use a **1** to include a field and **0** to exclude a field.

```JSON
db.posts.find({}, {_id: 0, title: 1, date: 1})
```
**Important!** You cannot use both 0 and 1 in the same object. The only exception is the **_id** field. You should either specify the fields you would like to include or the fields you would like to exclude.  

