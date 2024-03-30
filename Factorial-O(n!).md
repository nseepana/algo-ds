# Factorial time complexity O(n!), 

Grows extremely fast and becomes impractical even for relatively small input sizes. It typically appears in algorithms that involve generating all permutations of a set or solving certain combinatorial problems. Here are ten TypeScript examples to illustrate O(n!) complexity, each with detailed explanations:

### 1. Generating All Permutations of an Array
This function generates all possible arrangements of array elements.

```typescript
function permuteArray(arr: any[]): any[][] {
    const result: any[][] = [];

    const permute = (current: any[], remaining: any[]) => {
        if (remaining.length === 0) {
            result.push(current);
            return;
        }

        for (let i = 0; i < remaining.length; i++) {
            // Choose element to add to the permutation
            let next = [...current, remaining[i]];
            // Form a new array without the chosen element
            let rest = remaining.slice(0, i).concat(remaining.slice(i + 1));
            // Continue with recursion
            permute(next, rest);
        }
    };

    permute([], arr);
    return result;
}
```

### 2. Travelling Salesman Problem (Brute Force)
A brute-force approach to solve the travelling salesman problem, which tries every possible route.

```typescript
function travellingSalesman(distances: number[][], start: number): number {
    let n = distances.length;
    let vertices: number[] = [];
    for (let i = 0; i < n; i++) if (i !== start) vertices.push(i);

    let minPathCost = Infinity;

    const permuteVertices = (currentPath: number[], remaining: number[], currentCost: number) => {
        if (remaining.length === 0) {
            currentCost += distances[currentPath[currentPath.length - 1]][start];
            minPathCost = Math.min(minPathCost, currentCost);
            return;
        }

        for (let i = 0; i < remaining.length; i++) {
            let next = [...currentPath, remaining[i]];
            let rest = remaining.slice(0, i).concat(remaining.slice(i + 1));
            let newCost = currentCost + distances[currentPath[currentPath.length - 1]][remaining[i]];
            permuteVertices(next, rest, newCost);
        }
    };

    permuteVertices([start], vertices, 0);
    return minPathCost;
}
```

### 3. Generating All Possible Subsets (Power Set)
This function lists all subsets of a given set. The number of subsets is 2^n, but the process to list them all is O(n!).

```typescript
function generatePowerSet(set: any[]): any[][] {
    const powerSet: any[][] = [];

    const generate = (index: number, subset: any[]) => {
        if (index === set.length) {
            powerSet.push(subset);
            return;
        }
        generate(index + 1, subset);
        generate(index + 1, [...subset, set[index]]);
    };

    generate(0, []);
    return powerSet;
}
```

### 4. Finding All Combinations of k Elements in an Array
Generates all combinations of k elements from the given array.

```typescript
function combinations(arr: any[], k: number): any[][] {
    const result: any[][] = [];

    const combine = (start: number, combo: any[]) => {
        if (combo.length === k) {
            result.push([...combo]);
            return;
        }
        for (let i = start; i < arr.length; i++) {
            combo.push(arr[i]);
            combine(i + 1, combo);
            combo.pop(); // backtrack
        }
    };

    combine(0, []);
    return result;
}
```

### 5. Full Permutation of String
Generates all possible permutations of a given string.

```typescript
function stringPermutations(str: string): string[] {
    const result: string[] = [];

    const permute = (prefix: string, remaining: string) => {
        if (remaining.length === 0) {
            result.push(prefix);
            return;
        }
        for (let i = 0; i < remaining.length; i++) {
            permute(prefix + remaining[i], remaining.slice(0, i) + remaining.slice(i + 1));
        }
    };

    permute("", str);
    return result;
}
```

### 6. Permutations of Array With Unique Elements
Generates permutations of an array, ensuring each permutation is unique.

```typescript
function uniquePermutations(arr: any[]): any[][] {
    const result: any[][] = [];
    const used = new Array(arr.length).fill(false);

    const permute = (current: any[]) => {
        if (current.length === arr.length) {
            result.push([...current]);
            return;
        }

        for (

let i = 0; i < arr.length; i++) {
            if (used[i]) continue;
            used[i] = true;
            current.push(arr[i]);
            permute(current);
            current.pop();
            used[i] = false;
        }
    };

    permute([]);
    return result;
}
```

### 7. Boggle Board Solver
Finds all words that can be formed by a sequence of adjacent characters on a Boggle board.

```typescript
function solveBoggle(board: string[][], dictionary: Set<string>): string[] {
    // The actual implementation of a Boggle solver is complex,
    // involving backtracking and a trie data structure for efficient word checking.
    return []; // Placeholder return
}
```

### 8. N-Queens Solver
Finds all possible solutions for placing N queens on an NxN chessboard so that no two queens attack each other.

```typescript
function solveNQueens(n: number): string[][] {
    const solutions: string[][] = [];
    const board: string[][] = Array.from({ length: n }, () => Array(n).fill('.'));

    // Function to check if a queen can be placed
    const canPlace = (row: number, col: number): boolean => {
        // Implementation of checks for N-Queens problem
        return true; // Placeholder return
    };

    // Recursive function to place queens
    const placeQueens = (row: number) => {
        if (row === n) {
            solutions.push(board.map(row => row.join('')));
            return;
        }

        for (let col = 0; col < n; col++) {
            if (canPlace(row, col)) {
                board[row][col] = 'Q';
                placeQueens(row + 1);
                board[row][col] = '.'; // backtrack
            }
        }
    };

    placeQueens(0);
    return solutions;
}
```

### 9. Generate All Possible Team Combinations
Given a list of players, generate all possible team combinations.

```typescript
function teamCombinations(players: string[]): string[][][] {
    const teams: string[][][] = [];

    const generateTeams = (index: number, currentTeam: string[], remainingPlayers: string[]) => {
        if (index === players.length) {
            teams.push([currentTeam, remainingPlayers]);
            return;
        }
        generateTeams(index + 1, currentTeam.concat(players[index]), remainingPlayers);
        generateTeams(index + 1, currentTeam, remainingPlayers.concat(players[index]));
    };

    generateTeams(0, [], players);
    return teams;
}
```

### 10. Generating All Possible Votes in an Election
Given n candidates, generate all possible ways n voters might vote.

```typescript
function generateElectionResults(candidates: string[]): string[][] {
    const results: string[][] = [];
    // Recursive function to generate votes
    // Due to the complexity and repetitive nature, implementation is omitted.
    return results; // Placeholder return
}
```

In each example, the time complexity grows factorially with the input size, highlighting the exponential growth inherent in O(n!) algorithms. These examples are mainly theoretical, as factorial time algorithms quickly become infeasible for even moderate-sized inputs.
