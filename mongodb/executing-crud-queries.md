# Executing CRUD Queries using Mongoose

Start by installing Mongoose and establish a connection to your MongoDB database. Define a model by creating defining a schema. 

*Refer to [Object Data Modeling](/mongodb/object-data-modeling.md)*.

To create a new document, create a new instance of the model defined by the schema and call the `save()` method. This will save the document to the database:

```javascript
const userSchema = new mongoose.Schema({
    name: String,
    age: Number,
    email: String,
});

const User = mongoose.model('User', userSchema);

const newUser = new User({
    name: 'John Doe',
    age: 25,
    email: 'jdoe@example.com',
});

newUser.save()
    .then((savedUser) => {
        console.log('User created:', savedUser);
        // You can perform further operations on the saved user here
    })
    .catch((error) => {
        console.error('Failed to create user:', error);
    });
```

To retrieve documents, use methods like `find()` and `findOne()` on the model. These methods accept a query condition and return matching documents from the database:

```javascript
User.find({ age: 25 })
    .then((users) => {
        console.log('Users found:', users);
        // You can process the retrieved users here
    })
    .catch((error) => {
        console.error('Failed to find users:', error);
    });
```

To update documents, retrieve the desired documents and modify its properties. Call the `save()` method to persist the changes to the database:

```javascript 
User.findOne({ name: 'John Doe' })
    .then((user) => {
        user.age = 30; // Modify the age property
        return user.save(); // Save the changes
    })
    .then((updatedUser) => {
        console.log('User updated:', updatedUser);
        // You can perform further operations on the updated user here
    })
    .catch((error) => {
        console.error('Failed to update user:', error);
});
```

To delete documents, retrieve the desired documents and call the `remove()` method or `deleteOne()` method to remove it from the database:

```javascript
User.findOneAndDelete({ name: 'John Doe' })
    .then((deletedUser) => {
        console.log('User deleted:', deletedUser);
    })
```