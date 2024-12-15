# Data Structures and Algorithms (DSA) using JavaScript

## 2. Start with the Basics of DSA

### Understand the Fundamental Concepts:

#### Big-O Notation

Big-O notation is used to describe the performance of an algorithm. It helps measure:

- **Time Complexity**: How the runtime of an algorithm grows with the size of the input.
- **Space Complexity**: How the memory usage of an algorithm grows with the size of the input.

### Types of Big-O Notations with Examples:

1. **O(1) - Constant Time**:

   - The runtime does not depend on the input size.
   - Example:
     ```javascript
     function accessFirstElement(arr) {
       return arr[0]; // Always takes the same time
     }
     ```

2. **O(n) - Linear Time**:

   - The runtime grows linearly with the input size.
   - Example:
     ```javascript
     function printAllElements(arr) {
       for (let i = 0; i < arr.length; i++) {
         console.log(arr[i]);
       }
     }
     ```

3. **O(log n) - Logarithmic Time**:

   - The runtime grows logarithmically as the input size is reduced by a consistent fraction (e.g., halved).
   - Example: Binary Search
     ```javascript
     function binarySearch(arr, target) {
       let left = 0,
         right = arr.length - 1;
       while (left <= right) {
         const mid = Math.floor((left + right) / 2);
         if (arr[mid] === target) return mid;
         if (arr[mid] < target) left = mid + 1;
         else right = mid - 1;
       }
       return -1;
     }
     ```

4. **O(n²) - Quadratic Time**:

   - The runtime grows quadratically with the input size, often involving nested loops.
   - Example: Bubble Sort
     ```javascript
     function bubbleSort(arr) {
       for (let i = 0; i < arr.length; i++) {
         for (let j = 0; j < arr.length - i - 1; j++) {
           if (arr[j] > arr[j + 1]) {
             [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
           }
         }
       }
       return arr;
     }
     ```

5. **O(2ⁿ) - Exponential Time**:

   - The runtime doubles with each additional input size, often in recursive solutions.
   - Example: Fibonacci Sequence (Recursive)
     ```javascript
     function fibonacci(n) {
       if (n <= 1) return n;
       return fibonacci(n - 1) + fibonacci(n - 2);
     }
     ```

6. **O(n!) - Factorial Time**:
   - The runtime grows factorially, common in brute-force permutations or combinations.
   - Example: Permutations
     ```javascript
     function permutations(arr) {
       if (arr.length === 0) return [[]];
       const result = [];
       for (let i = 0; i < arr.length; i++) {
         const rest = [...arr.slice(0, i), ...arr.slice(i + 1)];
         for (const perm of permutations(rest)) {
           result.push([arr[i], ...perm]);
         }
       }
       return result;
     }
     ```

### Space Complexity:

- Measures the amount of memory used by an algorithm.
- Example (O(1) Space):
  ```javascript
  function sumArray(arr) {
    let sum = 0;
    for (let i = 0; i < arr.length; i++) {
      sum += arr[i];
    }
    return sum; // Memory usage does not grow with input size.
  }
  ```
- Example (O(n) Space):
  ```javascript
  function buildArray(n) {
    const result = [];
    for (let i = 0; i < n; i++) {
      result.push(i);
    }
    return result; // Memory usage grows with input size.
  }
  ```

## Summary Table of Common Big-O Complexities

| Big-O Notation | Name              | Example Use Case           |
| -------------- | ----------------- | -------------------------- |
| O(1)           | Constant Time     | Accessing an array element |
| O(log n)       | Logarithmic Time  | Binary Search              |
| O(n)           | Linear Time       | Iterating through an array |
| O(n log n)     | Linearithmic Time | Merge Sort, Quick Sort     |
| O(n²)          | Quadratic Time    | Nested loops               |
| O(2ⁿ)          | Exponential Time  | Recursive Fibonacci        |
| O(n!)          | Factorial Time    | Generating permutations    |
