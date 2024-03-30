# Quadratic time complexity

Algorithms that involve nested iterations over the data. Common examples include simple sorting algorithms, algorithms that involve checking pairs of elements, and more. Here are ten examples in TypeScript:

### 1. Bubble Sort
This sorting algorithm repeatedly swaps adjacent elements if they are in the wrong order.

```typescript
function bubbleSort(arr: number[]): number[] {
    let n = arr.length;
    for (let i = 0; i < n; i++) { // Outer loop goes through each element
        for (let j = 0; j < n - i - 1; j++) { // Inner loop for comparing adjacent elements
            if (arr[j] > arr[j + 1]) {
                // Swap if elements are in the wrong order
                [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
            }
        }
    }
    return arr;
}
```

### 2. Insertion Sort
This sorting algorithm builds the sorted array one item at a time.

```typescript
function insertionSort(arr: number[]): number[] {
    let n = arr.length;
    for (let i = 1; i < n; i++) { // Outer loop iterates through elements
        let current = arr[i];
        let j = i - 1;
        // Inner loop moves sorted elements greater than `current` up by one position
        while (j >= 0 && arr[j] > current) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = current; // Place `current` at its correct position
    }
    return arr;
}
```

### 3. Selection Sort
This algorithm repeatedly selects the minimum element and places it at the beginning.

```typescript
function selectionSort(arr: number[]): number[] {
    let n = arr.length;
    for (let i = 0; i < n; i++) { // Outer loop moves the boundary of unsorted subarray
        let minIndex = i;
        for (let j = i + 1; j < n; j++) { // Inner loop finds the minimum element
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        // Swap the found minimum element with the first element
        [arr[i], arr[minIndex]] = [arr[minIndex], arr[i]];
    }
    return arr;
}
```

### 4. Checking for Duplicates in an Array
This algorithm checks for duplicate elements in an array.

```typescript
function hasDuplicates(arr: number[]): boolean {
    let n = arr.length;
    for (let i = 0; i < n; i++) { // Iterate over array
        for (let j = i + 1; j < n; j++) { // Iterate over subsequent elements
            if (arr[i] === arr[j]) {
                // If a duplicate is found, return true
                return true;
            }
        }
    }
    return false; // If no duplicates found, return false
}
```

### 5. Matrix Multiplication
This algorithm multiplies two matrices.

```typescript
function matrixMultiply(A: number[][], B: number[][]): number[][] {
    let rowsA = A.length, colsA = A[0].length;
    let rowsB = B.length, colsB = B[0].length;
    let C = Array.from({ length: rowsA }, () => new Array(colsB).fill(0));

    for (let i = 0; i < rowsA; i++) { // Iterate over rows of A
        for (let j = 0; j < colsB; j++) { // Iterate over columns of B
            for (let k = 0; k < colsA; k++) { // Multiply and sum
                C[i][j] += A[i][k] * B[k][j];
            }
        }
    }
    return C;
}
```

### 6. Checking All Pairs for Sum
Check if any pair of numbers in the array sums up to a given value.

```typescript
function hasPairWithSum(arr: number[], sum: number): boolean {
    let n = arr.length;
    for (let i = 0; i < n; i++) { // Iterate over array
        for (let j = i + 1; j < n; j++) { // Iterate over every other element
            if (arr[i] + arr[j] === sum) {
                // If pair with the required sum is found
                return true;
            }
        }
    }
    return false; // If no pair with the required sum is found
}
```

### 7. Print All Pairs in Array
Print all possible pairs in an array.



```typescript
function printAllPairs(arr: number[]): void {
    let n = arr.length;
    for (let i = 0; i < n; i++) { // Iterate over array
        for (let j = 0; j < n; j++) { // Iterate over array again for each element
            console.log(arr[i], arr[j]); // Print the pair
        }
    }
}
```

### 8. Transpose of a Matrix
Calculate the transpose of a matrix.

```typescript
function transposeMatrix(matrix: number[][]): number[][] {
    let rows = matrix.length, cols = matrix[0].length;
    let transpose = Array.from({ length: cols }, () => new Array(rows).fill(0));

    for (let i = 0; i < rows; i++) { // Iterate over rows
        for (let j = 0; j < cols; j++) { // Iterate over columns
            transpose[j][i] = matrix[i][j]; // Swap elements
        }
    }
    return transpose;
}
```

### 9. Floyd's Triangle
Print Floyd's triangle, a right-angled triangular array of natural numbers.

```typescript
function floydsTriangle(rows: number): void {
    let number = 1;
    for (let i = 1; i <= rows; i++) { // Outer loop for each row
        for (let j = 1; j <= i; j++) { // Inner loop for each column
            process.stdout.write(number.toString() + " "); // Print the number
            number++; // Increment the number
        }
        console.log(); // New line after each row
    }
}
```

### 10. Naive String Matching
Check if a substring exists in a given string (naive approach).

```typescript
function naiveStringMatch(text: string, pattern: string): boolean {
    let n = text.length;
    let m = pattern.length;
    for (let i = 0; i <= n - m; i++) { // Iterate over the text
        let j;
        for (j = 0; j < m; j++) { // Iterate over the pattern
            if (text[i + j] !== pattern[j]) break; // Mismatch found
        }
        if (j === m) return true; // If full pattern was found
    }
    return false; // If pattern was not found
}
```

Each of these examples demonstrates an algorithm where the number of operations grows quadratically as the input size increases. In simple terms, for an input of size `n`, the algorithm might have to perform operations up to `n * n` times.
