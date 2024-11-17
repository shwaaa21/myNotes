# Code Principles Used
- **Reusable Functions**: Writing functions that can generate other functions to reduce redundancy and improve maintainability.
- **Closure**: Using the scope of an outer function to encapsulate data or behavior for the inner function.
- **Higher-Order Functions**: Creating functions that operate on or return other functions.

## Function Factories in JavaScript
### Greeting Function Factory

### Code
```javascript
function createGreeting(message) {
    return function(name) {
        return `${message}, ${name}!`;
    };
}

const hello = createGreeting("Hello");
console.log(hello("Alice")); // "Hello, Alice!"

const goodbye = createGreeting("Goodbye");
console.log(goodbye("Bob")); // "Goodbye, Bob!"
```

---

### Explanation of Code

1. **Outer Function: `createGreeting`**
   - Takes a single parameter, `message` (e.g., `"Hello"` or `"Goodbye"`).
   - Returns a new inner function.

2. **Inner Function**
   - Accepts one parameter, `name`.
   - Combines the `message` (from the outer function) with the `name` to create a personalized greeting string.
   - The inner function "remembers" the `message` from its outer function due to **closure**.

3. **Example Usage**
   - `createGreeting("Hello")` creates a new function that always starts greetings with `"Hello"`.
   - Assign the returned function to `hello` and call it with a name to generate a custom message.
   - Similarly, `createGreeting("Goodbye")` creates a different greeting function.

---

### Why Use Function Factories?

- **Eliminates Redundant Code**: Instead of writing separate greeting functions (e.g., `sayHello`, `sayGoodbye`), you write one reusable factory function.
- **Customizability**: The outer function allows you to easily generate specialized behavior (e.g., different greetings) without hardcoding.
- **Leverages Closure**: The inner function can access the variables (`message`) defined in the outer function, even after the outer function has executed.

---

### Applications
1. **API Call Factories**
   - Creating functions tailored to specific endpoints or data formats.
2. **Event Handlers**
   - Generating dynamic handlers for specific UI components.
3. **Configuration Generators**
   - Building functions that depend on external settings or environments.