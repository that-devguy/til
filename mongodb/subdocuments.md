# Subdocuments

Subdocuments in Mongoose allow you to nest schemas within other schemas. This provides a way to represent complex data structures and relationships in MongoDB.

To define an array of subdocuments, you can use the `Schema.Types.Array` type in Mongoose. Here's an example:

```javascript
const mongoose = require('mongoose');

const commentSchema = new mongoose.Schema({
  text: String,
  author: String
});

const postSchema = new mongoose.Schema({
  title: String,
  comments: [commentSchema] // Array of subdocuments
});

const Post = mongoose.model('Post', postSchema);
```

In the above example, the `Post` schema contains an array of `Comment` subdocuments. Each `Comment` subdocument has a `text` and `author` field.

**Single Nested Subdocuments**

To define a single nested subdocument, you can use the `Schema.Types.Embedded` type in Mongoose. Here's an example:

```javascript
const mongoose = require('mongoose');

const addressSchema = new mongoose.Schema({
  street: String,
  city: String,
  country: String
});

const userSchema = new mongoose.Schema({
  name: String,
  address: addressSchema // Single nested subdocument
});

const User = mongoose.model('User', userSchema);
```

In the above example, the `User` schema contains a single nested `Address` subdocument. The `Address` subdocument has fields like `street`, `city`, and `country`.

**Working with Subdocuments**

Once you have defined the subdocuments in your schemas, you can work with them like any other fields in your documents. You can create, modify, and access subdocuments using dot notation.

Here are some common operations you can perform with subdocuments:

- **Creating Subdocuments**:
  ```javascript
  const post = new Post({
    title: 'My First Post',
    comments: [
      { text: 'Great post!', author: 'John' },
      { text: 'Nice work!', author: 'Jane' }
    ]
  });
  ```

- **Accessing Subdocuments**:
  ```javascript
  const post = await Post.findById(postId);
  console.log(post.comments); // Access the comments subdocument array
  console.log(post.comments[0].text); // Access a specific comment
  ```

- **Modifying Subdocuments**:
  ```javascript
  const post = await Post.findById(postId);
  const comment = post.comments.id(commentId); // Access a specific comment by its _id
  comment.text = 'Updated comment';
  await post.save();
  ```

- **Removing Subdocuments**:
  ```javascript
  const post = await Post.findById(postId);
  post.comments.id(commentId).remove(); // Remove a specific comment
  await post.save();
  ```

Remember to save the parent document (`post` in the above examples) after making changes to the subdocuments.

Subdocuments in Mongoose provide a powerful way to model and work with nested data structures in MongoDB. They can help you represent complex relationships and organize your data effectively.
