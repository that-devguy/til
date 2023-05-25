# Virtuals

Virtuals are a feature provided by Mongoose that allows you to define properties or fields on a document that are not stored directly in the database but are computer or derived from other fields.

Virtuals are defined using Mongoose's schema virtuals API and can be useful in scenarios where you need to dynamically generate or transform data based on the existing fields within a document. They are not persisted in the database but can be accessed and utilized in your application's code as they were actual properties.

Example of adding a virtual property to a MongoDB document representing a user:

```javascript
const userSchema = new mongoose.Schema({
  firstName: String,
  lastName: String
});

// Define the virtual property
userSchema.virtual('fullName').get(function() {
  return `${this.firstName} ${this.lastName}`;
});

// Create and access the virtual property on a document
const User = mongoose.model('User', userSchema);
const user = new User({ firstName: 'John', lastName: 'Doe' });

console.log(user.fullName); // Output: "John Doe"
```

In this example, `fullName` is not stored as a separate field in the database, but it can be accessed and used like any other property on the `user` document. Virtuals can be helpful for simplifying data access and manipulation within your application by providing computed or derived properties based on the existing data in the document.