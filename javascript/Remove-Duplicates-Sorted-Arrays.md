# Code Principles Used
- **Two-pointer technique**: Uses two pointers (`i` and `k`) to iterate through the array efficiently.
- **In-place modification**: Modifies the array without using additional space, achieving a space complexity of O(1).
- **Sorted array property**: Leverages the sorted order of elements to identify and remove duplicates easily.

# Remove Duplicates from Sorted Array
## Problem Summary
Given an integer array `nums` sorted in non-decreasing order, remove duplicates in-place so that each unique element appears only once. The function should return the number of unique elements (`k`). The first `k` elements of `nums` should contain these unique elements in their original order, while the remaining elements do not matter.

### Example
Input: `nums = [1, 1, 2]`  
Output: `k = 2`, `nums = [1, 2, _]`

Input: `nums = [0,0,1,1,1,2,2,3,3,4]`  
Output: `k = 5`, `nums = [0, 1, 2, 3, 4, _, _, _, _, _]`

### Constraints
- `1 <= nums.length <= 3 * 10^4`
- `-100 <= nums[i] <= 100`
- `nums` is sorted in non-decreasing order.

### Code
```javascript
function removeDuplicates(nums) {
    let k = 1; // Start from 1 because the first element is always unique

    for (let i = 1; i < nums.length; i++) {
        if (nums[i] !== nums[i - 1]) { // Check if the current element is different from the previous
            nums[k] = nums[i]; // Place the unique element at index `k`
            k++; // Move the `k` pointer for the next unique element
        }
    }

    return k; // `k` is the count of unique elements
}
```

### Explanation of Code
1. **Initialize a Pointer**: We start `k` at 1 since the first element in a sorted array is always unique.
  
2. **Iterate with a Second Pointer**: We loop through `nums` with `i` starting from 1. In each iteration:
   - We check if `nums[i]` is different from `nums[i - 1]` (the previous element).
  
3. **Move Unique Elements to Front**:
   - If `nums[i]` is unique, we place it at `nums[k]`.
   - Then we increment `k` to prepare for the next unique element.
   
4. **Return the Count**: By the end, `k` holds the number of unique elements, and `nums` is modified in-place such that the first `k` elements are unique.