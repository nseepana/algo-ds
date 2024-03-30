# Linear time complexity (O(n)):

The time taken by an algorithm increases linearly with the size of the input. Here are ten examples in TypeScript with detailed explanations for each line:

### 1. Find Maximum in an Array
```typescript
function findMax(arr: number[]): number {
    if(arr.length === 0) return -Infinity; // Edge case: empty array
    let max = arr[0]; // Start with the first element as the max

    for(let i = 1; i < arr.length; i++) { // Iterate through the array starting from the second element
        if(arr[i] > max) { // If the current element is greater than the current max
            max = arr[i]; // Update max to the current element
        }
    }

    return max; // Return the maximum value found
}
```

### 2. Calculate Sum of Elements
```typescript
function sumArray(arr: number[]): number {
    let sum = 0; // Initialize sum as 0

    for(const value of arr) { // Loop over each element in the array
        sum += value; // Add the current element to the sum
    }

    return sum; // Return the total sum
}
```

### 3. Check for Element in Array
```typescript
function contains(arr: number[], target: number): boolean {
    for(const value of arr) { // Loop through each element
        if(value === target) { // Check if the current element is the target
            return true; // If found, return true
        }
    }

    return false; // If not found, return false
}
```

### 4. Count Occurrences of a Number
```typescript
function countOccurrences(arr: number[], target: number): number {
    let count = 0; // Initialize count to 0

    for(const value of arr) { // Iterate over each element
        if(value === target) { // Check if the current element equals the target
            count++; // Increment count
        }
    }

    return count; // Return the final count
}
```

### 5. Find the Index of an Element
```typescript
function indexOfElement(arr: number[], target: number): number {
    for(let i = 0; i < arr.length; i++) { // Loop through the array
        if(arr[i] === target) { // If the current element is the target
            return i; // Return the current index
        }
    }

    return -1; // If the target is not found, return -1
}
```

### 6. Check if Array is Sorted
```typescript
function isArraySorted(arr: number[]): boolean {
    for(let i = 1; i < arr.length; i++) { // Start from the second element
        if(arr[i] < arr[i - 1]) { // Check if the current element is less than the previous one
            return false; // If so, array is not sorted
        }
    }

    return true; // If the loop completes, the array is sorted
}
```

### 7. Reverse an Array
```typescript
function reverseArray(arr: number[]): number[] {
    let start = 0; // Starting index
    let end = arr.length - 1; // Ending index

    while(start < end) { // Loop until the start index is less than the end index
        let temp = arr[start]; // Temporary variable to hold the start element
        arr[start] = arr[end]; // Swap the start element with the end element
        arr[end] = temp; // Complete the swap
        start++; // Move the start index forward
        end--; // Move the end index backward
    }

    return arr; // Return the reversed array
}
```

### 8. Concatenate Two Arrays
```typescript
function concatenateArrays(arr1: number[], arr2: number[]): number[] {
    return [...arr1, ...arr2]; // Use spread operator to combine both arrays
}
```

### 9. Print Elements of an Array
```typescript
function printArray(arr: number[]): void {
    for(const value of arr) { // Loop over each element
        console.log(value); // Print the current element
    }
}
```

### 10. Calculate Average of Numbers
```typescript
function calculateAverage(arr: number[]): number {
    if(arr.length === 0) return 0; // Handle empty array edge case
    let sum = 0; // Initialize sum to 0

    for(const value of arr) { // Loop over each element
        sum += value; // Sum up the elements
    }

    return sum / arr.length; // Return the average
}
```

Each of these examples demonstrates a linear time operation, where the time complexity is directly proportional to the size of the input array. As the array size

 grows, the number of steps in the algorithm grows linearly.
