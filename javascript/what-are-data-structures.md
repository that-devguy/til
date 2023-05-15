# What are data structures?

A data structure is a format to organize, manage and store data in a way that allows efficient access and modification. More specificly, collection of data values, the relationships between them, and the functions or operations that can be applied to that data

There are many different types of data structures. Some are better than others under certain circumstances.

JavaScript has **primitive** and **non-primitive** data structures.
- **primitive** is default out of the box structures such as arrays and objects (able to tackle most programming tasks)

- **non-primitive** don't come by default and have to be written (handy for unique specific tasks)

## Most popular data structures

[Arrays](#arrays)<br>
[Objects](#objects)<br>
[Stacks](#stacks)<br>
[Queues](#queues)<br>
[Linked Lists](#linked-lists)<br>


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

## Stacks

Store info in the form of a list using **LIFO**(last in, first out). Elements can NOT be added or removed out of order, always has to follow the LIFO pattern.

*The undo/redo functionality many programs have.*

Example of a stack data structure with five methods:

```javascript
class Stack {
    constructor() {
        this.items = []; // initializes an empty array to store stack elements
    }

    push(element) { // adds an element to the top of the stack
        this.items.push(element); // adds the element to the end of the array (top of stack)
    }

    pop() { // removes the top element of the stack
        if (this.items.length === 0) { // checks if the stack is empty
            return "error - stack is empty";
        }
        return this.items.pop(); // remove and return the top element
    }

    peek() { // returns the top element of the stack with out removing it
        return this.items[this.items.length - 1]; // return last item in the array (top of stack)
    }

    isEmpty() { // checks for an empty stack
        return this.items.length === 0; // returns true is the stack is empty
    }

    size() { // returns the size of the stack
        return this.items.length; // returns length of the array (number of elements in the stack)
    }
}
```

Example use of this stack:

```javascript
const stack = new Stack();

stack.push(10);
stack.push(20);
stack.push(30);

console.log(stack.peek()); // 30

console.log(stack.pop()); // 30

console.log(stack.size()); // 2
```

Pros
- Simple and easy to understand.
- Fast operations with push, pop, and peek.
- Memory efficient.
- Useful for depth-first search, backtracking, and function call stacks.

Cons
- Simple data structure with limited functionality.
- Not suitable for complex data types.
- Can lead to **stack overflow**(error that occurs when a program tries to store more data on the call stack than it can handle)

## Queues

Similar to [stacks](#stacks) except that they follow **FIFO**(first in, first out).

Example queue usages are background tasks and printing/task processing.

Example of a queue data structure:

```javascript
class Queue {
  constructor() {
    this.items = []; // initialize an empty array to store the queue elements
  }

  enqueue(element) { // adds an element to the back of the queue
    this.items.push(element); // add the element to the end of the array (back of queue)
  }

  dequeue() { // removes the front element from the queue
    if (this.isEmpty()) { // check if the queue is empty
      return "error - queue is empty";
    }
    return this.items.shift(); // remove and return the first element in the array (which is the front of the queue)
  }

  front() { // returns the front element of the queue without removing it
    if (this.isEmpty()) { // check if the queue is empty
      return "error - queue is empty";
    }
    return this.items[0]; // return the first element in the array (which is the front of the queue)
  }

  isEmpty() { // checks if the queue is empty
    return this.items.length === 0; // return true if the length of the array is 0 (which means the queue is empty)
  }

  size() { // returns the number of elements in the queue
    return this.items.length; // return the length of the array (which is the number of elements in the queue)
  }
}
```

Example use of this queue:

```javascript
let myQueue = new Queue();

myQueue.enqueue(10);
myQueue.enqueue(20);
myQueue.enqueue(30);

console.log(myQueue.items); // [10, 20, 30]

myQueue.dequeue(); 
console.log(myQueue.items); // [20, 30]

console.log(myQueueu.front()); // 20

console.log(myQueue.size()); // 2
```

Pros
- Simple and easy to understand.
- Good for implementing algorithms that require FIFO, such as scheduling and resource allocation.

Cons
- Simple data structure with limited functionality.
- Can lead to resource starvation if one or more elements are blocking the queue.

## Linked Lists

Does not use physical placement of data in memory. Instead uses a refrencing system where elements are stored in nodes that contain a pointer to the next node. Allows for effecient insertion and removal of items without the need for reorganization.

There are two kinds of linked lists, **singly linked lists** and **doubly linked lists**.
- **singly linked lists** have only a single pointer that indicates the next node.
- **doubly linked lists** have two pointers, one that points to the next node and one that points to the previous node. Doubly linked lists also perform better with certain methods but consume more memory because of the two pointers.

Example of singly linked list: 

```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class LinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
  }

  append(value) { // adds a new node to the end of the linked list
    const newNode = new Node(value); // create a new node with the given value
    if (!this.head) { // if the linked list is empty, set the head and tail to the new node
      this.head = newNode;
      this.tail = newNode;
    } else { // otherwise, add the new node to the end of the list and update the tail
      this.tail.next = newNode;
      this.tail = newNode;
    }
  }

  print() { // prints the values of all nodes in the linked list
    let currentNode = this.head;
    while (currentNode) {
      console.log(currentNode.value);
      currentNode = currentNode.next;
    }
  }
}
```

Example using this linked list: 

```javascript
const myList = new LinkedList();
myList.append(10);
myList.append(20);
myList.append(30);
myList.print(); // output: 10 20 30
```

Example of a doubly linked list:

```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
    this.prev = null;
  }
}

class DoublyLinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
  }

  append(value) { // adds a new node to the end of the linked list
    const newNode = new Node(value); // create a new node with the given value
    if (!this.head) { // if the linked list is empty, set the head and tail to the new node
      this.head = newNode;
      this.tail = newNode;
    } else { // otherwise, add the new node to the end of the list and update the tail
      newNode.prev = this.tail;
      this.tail.next = newNode;
      this.tail = newNode;
    }
  }

  print() { // prints the values of all nodes in the linked list
    let currentNode = this.head;
    while (currentNode) {
      console.log(currentNode.value);
      currentNode = currentNode.next;
    }
  }
}
```

Pros
- Effecient for insertion and removal of new elements from unknown locations.
- Less complex than restructuring an array.

Cons
- Uses more memory.
- Inefficient at retrieving a specific element.
- Inefficient at traversing the list backwards.

