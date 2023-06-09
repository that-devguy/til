# Conditional Rendering

In React, you can conditionally render JSX using JS syntax like `if` statements, `&&` and `? :` operators.

Here's an example of a `PackingList` component that renders `Item`s that can be marked as packed or not:
```javascript
function Item({ name, isPacked }) {
    if (isPacked) {
        return <li className="item">{name} ✔</li>;
    }
    return <li className="item">{name}</li>;
}

export default function PackingList() {
    return (
        <section>
            <h1>My Packing List</h1>
            <ul>
                <Item
                    isPacked={true}
                    name="Camping chairs"
                />
                <Item
                    isPacked={true}
                    name="Hatchet"
                />
                <Item
                    isPacked={false}
                    name="Cooking supplies"
                />
            </ul>
        </section>
    );
}
```

In a situation where you want to render nothing you can return null:
```javascript
function Item({name, isPacked}) {
    if (isPacked) {
        return null;
    }
    return <li className="item">{name}</li>;
}
```

Example of this same component written as a **conditional(ternary) operator**:
```javascript
return (
    <li className="item">
        {isPacked ? name + '✔' : name}
    </li>
);
```

Example using another common shortcut with **logical AND operator (`&&`)**;
```javascript
return (
    <li className="item">
        {name} {isPacked && '✔'}
    </li>
);
```

