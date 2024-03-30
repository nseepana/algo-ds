# Exponential time complexity O(2^n) 

indicates that the time taken by an algorithm doubles with each additional element in the input. Such algorithms are often recursive, where each function call branches into two or more recursive calls. Here are some TypeScript examples demonstrating this concept:

### 1. Fibonacci Sequence (Recursive)
The Fibonacci sequence is a classic example where each call branches into two more calls.

```typescript
function fibonacci(n: number): number {
    if (n <= 1) return n; // Base case for 0 and 1
    return fibonacci(n - 1) + fibonacci(n - 2); // Recursive call for n-1 and n-2
}
```

### 2. Computing Powers of a Number (Recursive)
Computing powers can also be done in an exponential manner.

```typescript
function power(base: number, exponent: number): number {
    if (exponent === 0) return 1; // Base case: any number to the power of 0 is 1
    return base * power(base, exponent - 1); // Recursive call to calculate base^(exponent-1)
}
```

### 3. All Subsets of a Set
Finding all subsets of a set (the power set) is an O(2^n) operation.

```typescript
function powerSet(set: number[], index = 0): number[][] {
    if (index === set.length) return [[]]; // Base case: return empty set

    let num = set[index];
    let subsets = powerSet(set, index + 1);
    let totalSubsets = [];

    for (let subset of subsets) {
        totalSubsets.push([...subset]); // Add existing subset
        totalSubsets.push([...subset, num]); // Add new subset with current number
    }

    return totalSubsets;
}
```

### 4. Counting Binary Strings Without Consecutive 1s
Count all binary strings of length `n` without consecutive 1s.

```typescript
function countBinaryStrings(n: number): number {
    if (n <= 0) return 1; // Base case
    if (n === 1) return 2; // Base case

    return countBinaryStrings(n - 1) + countBinaryStrings(n - 2); // Recursive call
}
```

### 5. Tower of Hanoi Problem
The Tower of Hanoi is a classic problem that demonstrates exponential time complexity.

```typescript
function towerOfHanoi(n: number, fromRod: string, toRod: string, auxRod: string) {
    if (n === 1) {
        console.log(`Move disk 1 from rod ${fromRod} to rod ${toRod}`);
        return;
    }
    towerOfHanoi(n - 1, fromRod, auxRod, toRod);
    console.log(`Move disk ${n} from rod ${fromRod} to rod ${toRod}`);
    towerOfHanoi(n - 1, auxRod, toRod, fromRod);
}
```

### 6. Permutations of a String
Generating all permutations of a string is an exponential operation.

```typescript
function permute(str: string, l: number, r: number) {
    if (l === r) {
        console.log(str);
    } else {
        for (let i = l; i <= r; i++) {
            str = swap(str, l, i);
            permute(str, l + 1, r);
            str = swap(str, l, i); // backtrack
        }
    }
}

function swap(a: string, i: number, j: number): string {
    let temp;
    let charArray = a.split("");
    temp = charArray[i];
    charArray[i] = charArray[j];
    charArray[j] = temp;
    return charArray.join("");
}
```

### 7. Generating All Balanced Parentheses
Generating all combinations of well-formed parentheses is a classic example.

```typescript
function generateParenthesis(n: number): void {
    generate("", n, n);
}

function generate(p: string, left: number, right: number): void {
    if (left > right) return; // invalid state

    if (left === 0 && right === 0) {
        console.log(p);
    } else {
        if (left > 0) generate(p + "(", left - 1, right);
        if (right > 0) generate(p + ")", left, right - 1);
    }
}
```

### 8. Solving the N-Queens Problem
The N-Queens problem is a classic backtracking problem with exponential complexity.

```typescript
function solveNQueens(n: number): void {
    // Initial code to set up the problem and call the recursive function goes here
}
```

### 9. Finding All Hamiltonian Paths in a Graph
Finding all

 paths that visit each vertex exactly once in a graph can have exponential complexity.

```typescript
function findHamiltonianPaths(graph: number[][]): void {
    // Initial code to set up the problem and explore all paths
}
```

### 10. Enumerating all Possible Decodings of a Digit String
A problem similar to Fibonacci, where a string of digits can be interpreted in multiple ways.

```typescript
function numDecodings(s: string): number {
    if (s.length === 0) return 0;
    return decode(s, 0);
}

function decode(s: string, index: number): number {
    if (index === s.length) return 1;
    if (s.charAt(index) === '0') return 0;

    let ans = decode(s, index + 1);
    if (index < s.length - 1 && (s.charAt(index) === '1' || (s.charAt(index) === '2' && s.charAt(index + 1) < '7'))) {
        ans += decode(s, index + 2);
    }

    return ans;
}
```

Each of these examples has an exponential increase in the number of operations as the input size increases, characteristic of O(2^n) complexity. This makes them impractical for large inputs.
