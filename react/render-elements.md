# Render Elements

1. Import React in your JS file:
```javascript
import React from 'react';
```

2. Define a new component by creating a JS function or class that returns **JSX** (syntax extension for JS used in React). Here's an example of a function component and class component:
- Function component:
```javascript
function MyComponent() {
    return (
        <h1>Hello, React!</h1>
    );
}
```
- Class component:
```javascript
class MyComponent extends React.Component {
    render() {
        return (
            <h1>Hello, React!</h1>
        );
    }
}
```

3. Next render the component using the `ReactDOM.render()` method to render your component into the target element:
```javascript
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(<MyComponent />, document.getElementById('root')); // Render the componenet into the target element
```

4. React will automatically update the DOM and reflect the changes to your componenet's JSX or data

**React components can only return a single element. If you want return multiple elements from a component's render method or function, you need to enclose them within a single parent element.**

Here's an example:
```javascript
function MyComponent() {
  return (
    <div>
      <h1>Hello, React!</h1>
      <p>This is a paragraph.</p>
      <button>Click me</button>
    </div>
  );
}
```
