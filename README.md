# MongoDB Cheatsheet

## Basics

* **MongoDB**: NoSQL database for storing JSON-like documents.
* **Key Concepts**:

  * Database: A collection of collections.
  * Collection: A group of documents.
  * Document: A record in MongoDB, stored as a JSON object.

---

## Common Commands

### Starting MongoDB

* Start MongoDB server:

  ```bash
  mongod
  ```
* Connect to MongoDB shell:

  ```bash
  mongo
  ```

### Database Operations

* Show all databases:

  ```javascript
  show dbs
  ```
* Use a specific database:

  ```javascript
  use <database_name>
  ```
* Check the current database:

  ```javascript
  db
  ```
* Drop a database:

  ```javascript
  db.dropDatabase()
  ```

### Collection Operations

* Show all collections:

  ```javascript
  show collections
  ```
* Create a collection:

  ```javascript
  db.createCollection('collection_name')
  ```
* Drop a collection:

  ```javascript
  db.collection_name.drop()
  ```

---

## CRUD Operations

### Insert

* Insert a single document:

  ```javascript
  db.collection_name.insertOne({ key: value })
  ```
* Insert multiple documents:

  ```javascript
  db.collection_name.insertMany([{ key1: value1 }, { key2: value2 }])
  ```

### Read

* Find all documents:

  ```javascript
  db.collection_name.find()
  ```
* Find documents with a filter:

  ```javascript
  db.collection_name.find({ key: value })
  ```
* Find one document:

  ```javascript
  db.collection_name.findOne({ key: value })
  ```
* Projection (select specific fields):

  ```javascript
  db.collection_name.find({ key: value }, { field1: 1, field2: 0 })
  ```

### Update

* Update one document:

  ```javascript
  db.collection_name.updateOne(
    { filter_key: value },
    { $set: { update_key: new_value } }
  )
  ```
* Update multiple documents:

  ```javascript
  db.collection_name.updateMany(
    { filter_key: value },
    { $set: { update_key: new_value } }
  )
  ```
* Replace a document:

  ```javascript
  db.collection_name.replaceOne(
    { filter_key: value },
    { key: new_value }
  )
  ```

### Delete

* Delete one document:

  ```javascript
  db.collection_name.deleteOne({ key: value })
  ```
* Delete multiple documents:

  ```javascript
  db.collection_name.deleteMany({ key: value })
  ```

---

## Query Operators

* Comparison:

  * `$eq`: Equal to
  * `$ne`: Not equal to
  * `$gt`: Greater than
  * `$gte`: Greater than or equal to
  * `$lt`: Less than
  * `$lte`: Less than or equal to
* Logical:

  * `$and`: Logical AND
  * `$or`: Logical OR
  * `$not`: Logical NOT
* Example:

  ```javascript
  db.collection_name.find({ $and: [ { key1: value1 }, { key2: value2 } ] })
  ```

---

## Aggregation Framework

* Aggregation stages:

  * `$match`: Filter documents.
  * `$group`: Group documents.
  * `$sort`: Sort documents.
  * `$project`: Transform documents.
* Example:

  ```javascript
  db.collection_name.aggregate([
    { $match: { key: value } },
    { $group: { _id: "$group_key", total: { $sum: "$field" } } },
    { $sort: { total: -1 } }
  ])
  ```

---

## Indexing

* Create an index:

  ```javascript
  db.collection_name.createIndex({ key: 1 })
  ```
* Drop an index:

  ```javascript
  db.collection_name.dropIndex({ key: 1 })
  ```
* View all indexes:

  ```javascript
  db.collection_name.getIndexes()
  ```

---

## Miscellaneous

* Count documents:

  ```javascript
  db.collection_name.countDocuments({ key: value })
  ```
* Rename a collection:

  ```javascript
  db.collection_name.renameCollection('new_name')
  ```
* Backup database:

  ```bash
  mongodump --db <database_name>
  ```
* Restore database:

  ```bash
  mongorestore --db <database_name> <backup_directory>
  ```
