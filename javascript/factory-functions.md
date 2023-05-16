# Factory Functions

A function that returns an object. A little "*factory*" that creates and returns new objects based on a template.

With a factory function, we can avoid repeating code for creating objects. Instead, we have a single function that handles the object creation process. Other benefits include private data and simplicity. Encapsulation helps in maintaining data privacy and prevents unwanted modifications. In general, factory functions are easier to understand and work with compared to classes or complex object-oriented concepts.

Example factory function:

```javascript
function createUser(name, age, city) { // Create function that accepts three arguments; name, age, city.
    const user = { // User object and map the function arguements to a key in the object
        name: name,
        age: age,
        city: city,
    }

    return { // Return two inner functions
        introduceSelf: function () {
            return console.log(`Hi my name is ${user.name} and I am currently ${user.age} years old.`);
        },

        location: function () {
            return console.log(`${user.name} is located in ${user.city}.`);
        }
    }
}

const beverly = createUser('Beverly', 58, 'Phoenix'); // Create a new user
const jim = createUser('Jim', 62, 'Ohio');

beverly.introduceSelf(); // Hi my name is Beverly and I am currently 58 years old.
jim.location(); // Jim is located in Ohio.
```

In this example we define a function called `createUser` that accepts three arguements: `name`, `age`, and `city`. Instead of using a class, our function creates and returns an object with two inner functions.

Inside `createUser` we create an object called `user` and map the arguements to keys in the object.

Our `createUser` function then returns another object that contains two inner functions: `introduceSelf` and `location`.

To create a user all we need to do is call the `createUser` function and pass the respective arguements for `name`, `age`, and `city` and assign it to a variable. In this case `beverly` and `jim`.