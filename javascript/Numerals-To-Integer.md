# Code Principles Used
- **Mapping Values**: Using a `Map` data structure to store the value of each Roman numeral character.
- **Conditional Logic for Subtraction**: If a smaller numeral is placed before a larger numeral, the smaller numeral is subtracted from the total instead of added.
- **Looping and Lookup**: Iterating through the string and using `Map.get()` for efficient lookups of numeral values.

## Roman Numerals to Integer Conversion
### Problem Summary
Given a string representing a Roman numeral, convert it to an integer. Roman numerals use specific symbols and combinations to denote numbers, sometimes placing smaller symbols before larger ones to indicate subtraction (e.g., "IV" for 4). This solution iterates through the string and adjusts the total based on the subtraction rules.

### Code
```javascript
/**
 * @param {string} s
 * @return {number}
 */
const romanToInt = function(s) {
    // Define the Roman numeral values using a Map
    const numerals = new Map([
        ["I", 1],
        ["V", 5],
        ["X", 10],
        ["L", 50],
        ["C", 100],
        ["D", 500],
        ["M", 1000]
    ]);

    let total = 0;

    // Loop through each character in the string
    for (let i = 0; i < s.length; i++) {
        // Get the current and next numeral values
        let current = numerals.get(s[i]);
        let next = numerals.get(s[i + 1]);

        // Check for subtraction case
        if (current < next) {
            total -= current;
        } else {
            total += current;
        }
    }

    return total;
};
```

### Explanation of Code
1. **Define Roman Numeral Values**: A `Map` stores each Roman numeral and its corresponding integer value, enabling efficient lookup.
2. **Initialize Total**: `total` will store the final integer result.
3. **Loop Through String**: For each character in the input string `s`:
   - **Lookup Current and Next Values**: Retrieve the integer values for the current and next characters using `numerals.get()`.
   - **Apply Subtraction Rule**: If `current` is smaller than `next`, subtract `current` from `total`. Otherwise, add `current` to `total`.
4. **Return Total**: After completing the loop, `total` holds the integer equivalent of the Roman numeral.