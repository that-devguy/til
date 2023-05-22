# Object Data Modeling

In MongoDB you can define the structure of a database and enforce data validation using schema and validators when using an **Object Data Modeling (ODM)** library like **Mongoose**.

Start by installing Mongoose:

```javascript
npm install mongoose
```

Next import Mongoose and establish a connection to your MongoDB database:

```javascript
const mongoose = require('mongoose');

// MongoDB connection URL and options
const url = 'mongodb://localhost:27017/your-database-name';
const options = {
    useNewUrlParser: true,
    useUnifiedTopology: true,
};

// Connect to the MongoDB database
mongose.connect(url, options)
    .then(() => console.log('Connected to MongoDB'))
    .catch((error) => console.error('Failed to connect to MongoDB:', error));
```

Define a schema using Mongoose's Schema class and define the fields with their types and additional properties:

```javascript
const { Schema } = mongoose;

const userSchema = new Schema({
    name: {
        type: String,
        required: true,
    },
    email: {
        type: String,
        required: true,
        unique: true,
        match: `/^([a-z0-9_\.-]+)@([a-z\.-]+)\.([a-z\.]{2,6})$/`,
    },
    age: {
        type: Number,
        min: 18,
        max: 100,
    },
});
```

Create a model based on the schema using Mongoose's model method:

```javascript
const User = mongoose.model('User', userSchema);
```

Use the model to perform database operations:
```javascript
// Create a new user
const newUser = new User({
    name: 'John Doe',
    email: 'john.doe@gmail.com',
    age: 25,
});

newUser.save();
    .then(() => console.log('User created successfully'))
    .catch((error) => console.error('Failed to create user:', error));
```

In this example we define a user schema with fields like `name`, `email`, and `age`, along with their types and validators. 

Mongoose's validators, such as `required`, `unique`, and `match`, enforce data validation rules.

