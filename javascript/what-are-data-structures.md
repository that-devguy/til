# What are data structures?

A data structure is a format to organize, manage and store data in a way that allows efficient access and modification. More specificly, collection of data values, the relationships between them, and the functions or operations that can be applied to that data

There are many different types of data structures. Some are better than others under certain circumstances.

JavaScript has **primitive** and **non-primitive** data structures.
- **primitive** is default out of the box structures such as arrays and objects (able to tackle most programming tasks)

- **non-primitive** don't come by default and have to be written (handy for unique specific tasks)

## Most popular data structures

[Arrays](#arrays)<br>
[Objects](#objects)<br>


## Arrays

A collection of items stored at contiguous memory locations(data elements stored in adjacent memory addresses)

**index** - Items are accessed through index number. Arrays always start at index 0, in an array of 4 elements you can access the 3rd element using index 2.

```javascript
const arr = ['cat', 'dog', 'bird', 'cow']
console.log(arr[2]) // bird
```

**length** - Length of an array is determined by the number of elements in the array. Our example has a length of 4.

```javascript
const arr = ['cat', 'dog', 'bird', 'cow']
console.log(arr.length) // 4
```

JavaScript can store values of any type and length can be dynamic.

```javascript
const arr = ['cat', 1, 'dog', 2, 'bird', 3, 'cow', 4]
```

**multidimensional array** - An array that has other arrays in inside itself.

```javascript
const arr = [
    [1, 2, 3],
    ['cat', 'dog', 'bird'],
    ['cat', 1, 'dog'],
]
```

Pros
- Easy to use.
- Good for adding/deleting elements from the end.
- Fast access because the elements are in contiguous memory locations.

Cons
- Underperforms other data strucutres when you need to add/delete from any part of the data structure.
- Not suited for associative data.
- Limited functionality.

## Objects

An object is a collection of key-value pairs(each element consists of a key and its corresponding value)

Also called **map**, **dictionary** or **hash-table** in other languages.

Example object where each key represents a student ID, and the corresponding value is the students name:

```javascript
const studentData = {
    1234: "Alice",
    2345: "Bob",
    3456: "Charlie",
}
```

Can store values and functions, values are refered to as properties and functions are refered to as methods.

```javascript
const studentData = {
    1234: "Alice",
    2345: function(){
        console.log("Bob")
    },
}
```

How to access properties and methods:

```javascript
console.log(studentData.1234) // Alice
console.log(studentData["1234"]) // Alice
studentData.2345() // Bob
```

Syntax for assigning new values: 

```javascript
studentData.1234 = "Adam"
studentData["1234"] = "Adam"
studentData.2345 = () => console.log("David")

console.log(studentData.1234) // Adam
console.log(studentData["1234"]) // Adam
studentData.2345() // David
```

Example object containing key-value pairs:

```javascript
const studentData = {
    1234: { name: "Alice", age: 18, grade: "A" },
    2345: { name: "Bob", age: 17, grade: "B" },
    3456: { name: "David", age: 18, grade: "D" },
}
```

Pros
- Easy to use.
- Good way to group together data that is related.
- Good for separating data based on a unique condition.
- Object-oriented programming.

Cons
- Can be less efficient than other data structures for certain operations, such as iterating over large collections of data.
- Can become complex and difficult to manage if they contain large quantities of properties or nested objects.


