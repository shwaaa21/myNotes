# Code Principles Used  
- **Nested Loops for 2D Arrays**: Iterating over rows and columns of a matrix.  
- **Row Sum Calculation**: Calculating the sum of each row to determine customer wealth.  
- **Comparison for Maximum Value**: Keeping track of the maximum wealth seen so far.  

## Finding the Maximum Wealth in a 2D Array  
### Problem Summary  
Given a 2D array where each row represents the wealth of a customer across multiple accounts, determine the maximum wealth among all customers. The wealth of a customer is the sum of the integers in their row.  

**Example Input/Output**:  
- **Input**:  
  `accounts = [[1,2,3],[3,2,1]]`  
  Each row represents a customer's accounts.  
- **Output**: `6`  
  Explanation:  
  - Customer 1's wealth: `1 + 2 + 3 = 6`  
  - Customer 2's wealth: `3 + 2 + 1 = 6`  
  Both have wealth of 6, so the maximum wealth is `6`.  

---

### Code  
```javascript  
/**
 * @param {number[][]} accounts
 * @return {number}
 */
var maximumWealth = function(accounts) {
    let maxWealth = 0;

    // Iterate over each customer (row in the 2D array)
    for (let customer of accounts) {
        // Calculate the total wealth for this customer
        let currentWealth = customer.reduce((sum, account) => sum + account, 0);

        // Update maxWealth if this customer's wealth is higher
        if (currentWealth > maxWealth) {
            maxWealth = currentWealth;
        }
    }

    return maxWealth;
};
```

---

### Explanation of Code  
1. **Initialization**: `maxWealth` is set to 0 to store the maximum wealth found so far.  
2. **Iterating Over Rows**: Use a `for...of` loop to access each row (customer) in the 2D array.  
3. **Calculate Row Sum**: Use the `.reduce()` method to sum up all accounts in the row, representing the total wealth for that customer.  
4. **Update Maximum Wealth**: Compare the current customer's wealth with `maxWealth` and update `maxWealth` if the current wealth is greater.  
5. **Return Result**: After iterating through all rows, return the value of `maxWealth`, which is the maximum wealth among all customers.  

This approach efficiently calculates the maximum sum across rows, ensuring the solution is straightforward and clear for 2D array traversal and sum computation.