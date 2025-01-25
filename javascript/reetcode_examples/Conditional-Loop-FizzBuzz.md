# Code Principles Used
- **Conditional Logic**: Use `if-else` statements to check multiple conditions (divisibility by 3, 5, or both).
- **Loops**: Iterate through numbers from 1 to `n` to evaluate each number.
- **String Concatenation**: Combine strings ("Fizz" and "Buzz") dynamically based on conditions.
- **Efficiency**: Avoid redundant checks and keep the logic clear for maintainability.

## Using Conditional Logic and Loops for FizzBuzz
### Problem Summary
Given an integer `n`, return an array where:
- Each number divisible by 3 is replaced with "Fizz".
- Each number divisible by 5 is replaced with "Buzz".
- Numbers divisible by both 3 and 5 are replaced with "FizzBuzz".
- Numbers that do not meet these conditions are returned as their string representations.

This problem demonstrates the use of conditional logic to evaluate divisibility and dynamic string concatenation for flexible output.

### Code
```javascript
/**
 * @param {number} n
 * @return {string[]}
 */
const fizzBuzz = function(n) {
    const result = [];

    for (let i = 1; i <= n; i++) {
        let output = "";

        // Check divisibility and concatenate strings dynamically
        if (i % 3 === 0) output += "Fizz";
        if (i % 5 === 0) output += "Buzz";

        // If no conditions are met, use the number itself
        result.push(output || String(i));
    }

    return result;
};
```

### Explanation of Code
1. **Initialize Result Array**: Create an empty array `result` to store the output strings.
2. **Iterate Through Numbers**: Use a `for` loop to iterate from 1 to `n`.
3. **Dynamic String Construction**:
   - Initialize `output` as an empty string for each number.
   - Append "Fizz" if the number is divisible by 3.
   - Append "Buzz" if the number is divisible by 5.
4. **Fallback to Number**:
   - If `output` is still an empty string (no conditions met), add the number itself (converted to a string).
5. **Add to Result**: Push the constructed `output` to the `result` array.
6. **Return Result**: After the loop, return the `result` array containing the final FizzBuzz strings.

This approach is concise and maintains flexibility by dynamically constructing the string for each number. It avoids repetitive conditions and keeps the logic clear.