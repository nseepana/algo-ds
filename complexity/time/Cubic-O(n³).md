# Cubic-O(n³)

Occurs in algorithms where the time complexity is proportional to the cube of the input size. This is often seen in algorithms that involve triple nested loops over the input. Here are ten TypeScript examples illustrating cubic time algorithms, with explanations for each line of code.

### 1. Triple Nested Loop
A simple example of a triple nested loop iterating through elements.

```typescript
function tripleNestedLoop(n: number): void {
    for (let i = 0; i < n; i++) { // First loop
        for (let j = 0; j < n; j++) { // Second loop
            for (let k = 0; k < n; k++) { // Third loop
                console.log(i, j, k); // Operation performed on each combination of i, j, k
            }
        }
    }
}
```

### 2. Matrix Multiplication
Multiplying two matrices involves a triple loop, which is a classic O(n³) operation.

```typescript
function matrixMultiplication(a: number[][], b: number[][]): number[][] {
    const rowsA = a.length, colsA = a[0].length;
    const rowsB = b.length, colsB = b[0].length;
    let result = Array.from({ length: rowsA }, () => new Array(colsB).fill(0));

    for (let i = 0; i < rowsA; i++) {
        for (let j = 0; j < colsB; j++) {
            for (let k = 0; k < colsA; k++) {
                result[i][j] += a[i][k] * b[k][j]; // Multiply and sum
            }
        }
    }

    return result;
}
```

### 3. Checking for Substrings
Checking all substrings of a string within another string can be done in cubic time.

```typescript
function checkAllSubstrings(str: string, sub: string): boolean {
    for (let i = 0; i < str.length; i++) {
        for (let j = i; j < str.length; j++) {
            for (let k = j; k <= str.length; k++) {
                if (str.substring(i, k) === sub) {
                    return true; // Return true if substring is found
                }
            }
        }
    }
    return false;
}
```

### 4. 3-Sum Problem
The 3-sum problem finds if any three numbers in an array sum up to a given number.

```typescript
function threeSum(nums: number[], target: number): boolean {
    for (let i = 0; i < nums.length; i++) {
        for (let j = i + 1; j < nums.length; j++) {
            for (let k = j + 1; k < nums.length; k++) {
                if (nums[i] + nums[j] + nums[k] === target) {
                    return true; // Return true if a triplet with given sum is found
                }
            }
        }
    }
    return false;
}
```

### 5. Bubble Sort with Triple Loop
An inefficient version of bubble sort using a triple loop.

```typescript
function bubbleSortInefficient(arr: number[]): number[] {
    for (let i = 0; i < arr.length; i++) {
        for (let j = 0; j < arr.length - i - 1; j++) {
            for (let k = 0; k < arr.length - j - 1; k++) {
                if (arr[k] > arr[k + 1]) {
                    [arr[k], arr[k + 1]] = [arr[k + 1], arr[k]]; // Swap elements
                }
            }
        }
    }
    return arr;
}
```

### 6. Floyd Warshall Algorithm (All Pairs Shortest Path)
Floyd Warshall algorithm computes shortest paths between all pairs of vertices in a graph, which is O(n³).

```typescript
function floydWarshall(graph: number[][]): number[][] {
    let dist = graph.map(row => [...row]); // Clone the graph matrix

    let V = graph.length;
    for (let k = 0; k < V; k++) {
        for (let i = 0; i < V; i++) {
            for (let j = 0; j < V; j++) {
                if (dist[i][k] + dist[k][j] < dist[i][j]) {
                    dist[i][j] = dist[i][k] + dist[k][j]; // Update distance
                }
            }
        }
    }

    return dist;
}
```

### 7. Cubic Sum
Calculating the sum of all triplets (i, j, k) such that i

 + j + k = n.

```typescript
function cubicSum(n: number): number {
    let sum = 0;
    for (let i = 0; i <= n; i++) {
        for (let j = 0; j <= n; j++) {
            for (let k = 0; k <= n; k++) {
                if (i + j + k === n) {
                    sum++; // Increment sum for each valid triplet
                }
            }
        }
    }
    return sum;
}
```

### 8. Generating Cubic Combinations
Generate all combinations of three different elements from an array.

```typescript
function cubicCombinations(arr: number[]): number[][] {
    let combinations: number[][] = [];
    for (let i = 0; i < arr.length; i++) {
        for (let j = i + 1; j < arr.length; j++) {
            for (let k = j + 1; k < arr.length; k++) {
                combinations.push([arr[i], arr[j], arr[k]]); // Store the combination
            }
        }
    }
    return combinations;
}
```

### 9. Counting Triplets with a Given Sum
Count the number of triplets in an array that sum up to a specific value.

```typescript
function countTriplets(arr: number[], sum: number): number {
    let count = 0;
    for (let i = 0; i < arr.length; i++) {
        for (let j = i + 1; j < arr.length; j++) {
            for (let k = j + 1; k < arr.length; k++) {
                if (arr[i] + arr[j] + arr[k] === sum) {
                    count++; // Increment count for each valid triplet
                }
            }
        }
    }
    return count;
}
```

### 10. Nested Loop for Three-Dimensional Coordinates
Generating a list of all possible coordinates in a three-dimensional space with a given range.

```typescript
function generate3DCoordinates(limit: number): void {
    for (let x = 0; x <= limit; x++) {
        for (let y = 0; y <= limit; y++) {
            for (let z = 0; z <= limit; z++) {
                console.log(`Coordinate: (${x}, ${y}, ${z})`);
            }
        }
    }
}
```

Each of these examples demonstrates an algorithm where the number of operations increases cubically with the input size, characteristic of O(n³) complexity. These algorithms can quickly become impractical as the input size grows, due to their high computational demands.
