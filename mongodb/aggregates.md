# Aggregates

Aggregates in Mongoose allow you to perform advanced data processing operations on MongoDB collections. They enable you to combine, transform, and analyze data using various stages and operators.

**Performing Aggregations**

To perform aggregations in Mongoose, you can use the `aggregate()` method on your model. Here's an example:

```javascript
const mongoose = require('mongoose');

const bookSchema = new mongoose.Schema({
  title: String,
  author: String,
  genre: String,
  publishedYear: Number
});

const Book = mongoose.model('Book', bookSchema);

// Example aggregate query
Book.aggregate([
  { $match: { genre: 'Fiction' } },
  { $group: { _id: '$author', count: { $sum: 1 } } }
])
  .then(results => {
    console.log(results);
  })
  .catch(error => {
    console.error(error);
  });
```

In the above example, we perform an aggregation query on the `Book` model. We use the `$match` stage to filter books of a specific genre ('Fiction') and the `$group` stage to group books by author and count the number of books per author.

**Common Aggregate Operators**

- `$match`: Filters documents based on specified criteria.
- `$group`: Groups documents by specified fields and performs aggregations on grouped data.
- `$project`: Projects specific fields from documents and includes computed fields.
- `$sort`: Sorts documents based on specified criteria.
- `$limit`: Limits the number of documents in the result set.
- `$skip`: Skips a specified number of documents in the result set.
- `$lookup`: Performs a left outer join with another collection.
- `$unwind`: Deconstructs an array field into multiple documents.

These are just a few examples of the operators available for aggregations in Mongoose. You can combine and customize stages and operators to meet your specific data processing needs.