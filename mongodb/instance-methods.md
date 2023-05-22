# Instance Methods

Methods that are defined on individual documents or objects of a particular collection. Specific to the *instance* of the document and can be used to perform operations or access data related to the specific document.

Instance methods can be used to encapsulate document-specific logic and perform operations such as data manipulation, validation, or custom logic. They provide a convenient way to work with individual documents and interact with their data.


Here's an example of defining an instance method for a User collection:

```javascript
// Require Mongoose
const mongoose = require('mongoose');

// Define the User schema
const userSchema = new mongoose.Schema({
    firstName: String,
    lastName: String,
    // Other fields...
});

// Define the instance method on the schema
userSchema.methods.getFullName = function() {
    // `this` refers to the individual document instance
    // Concatenate the first name and last name fields to get the full name
    return this.firstName + ' ' + this.lastName;
};

// Create the User model using the schema
const User = mongoose.model('User', userSchema);

// Usage example
const user = new User({
    firstName: 'John',
    lastName: 'Doe',
});

// Call the instance method to get the full name
const fullName = user.getFullName();
console.log(fullName); // Output: John Doe
```

In this example, we define `getFullName` on the User schema. This methods gets the `firstName` and `lastName` fields and returns the full name. Then we create a User instance and call the `getFullName` method on that instance to retrieve the full name.