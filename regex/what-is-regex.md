# What is Regex?

**Regex(regular expression)** is a sequence of characters that defines a specific search pattern. They provide a concise and flexible way to search, extract and replace specific patterns within strings.

Regular expressions are commonly used for:
- Validating and extracting specific patterns from input strings(email adresses and phone numbers).
- Searching and replacing specific patterns within text.
- Splitting strings into meaningful parts.
- Performing complex text manipulations.

*Regular expressions can become more complex and include various combinations and rules depending on the specific requirements.*

Here's a few examples of regular expressions:
- Matching a Hex Value `/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`
- Matching an Email Address `/^([a-z0-9_\.-]+)@([a-z\.-]+)\.([a-z\.]{2,6})$/`
- Matching a URL `/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`
- Matching an HTML Tag `/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`

Here's an example that illustrates the concept:

```javascript
const text = "Hello, my email is zach@example.com. Feel free to contact me."

const pattern = /^([a-z0-9_\.-]+)@([a-z\.-]+)\.([a-z\.]{2,6})$/;

const email = text.match(pattern);
console.log(email); // zach@example.com
```

In this example we have a text string that includes an email address and define a regex pattern to match email addresses.

The `match` function is used to search for matches of the regex pattern inside the `text` string and returns any matches.

In this example the return is `zach@example.com`.

