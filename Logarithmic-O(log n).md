Logarithmic - O(log n):

Certainly! Logarithmic time complexity (O(log n)) typically appears in algorithms that divide the problem size in each step, instead of dealing with it as a whole. Common scenarios include certain types of searching algorithms, especially those on sorted data structures. Below are ten examples in TypeScript that demonstrate logarithmic time complexity:

### 1. Binary Search
```typescript
function binarySearch(arr: number[], target: number): number {
    let low = 0;
    let high = arr.length - 1;

    while (low <= high) {
        let mid = Math.floor((low + high) / 2);
        if (arr[mid] === target) {
            return mid;
        } else if (arr[mid] < target) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }
    return -1;
}
```

### 2. Finding an Element in a Balanced Binary Search Tree
```typescript
class TreeNode {
    value: number;
    left: TreeNode | null;
    right: TreeNode | null;

    constructor(value: number) {
        this.value = value;
        this.left = null;
        this.right = null;
    }
}

function searchBST(root: TreeNode | null, key: number): boolean {
    if (root === null) return false;
    if (root.value === key) return true;

    return key < root.value ? searchBST(root.left, key) : searchBST(root.right, key);
}
```

### 3. Finding the Height of a Balanced Binary Tree
```typescript
function heightOfBST(root: TreeNode | null): number {
    if (root === null) return -1;
    return 1 + Math.max(heightOfBST(root.left), heightOfBST(root.right));
}
```

### 4. Calculating the Greatest Common Divisor (Euclidean Algorithm)
```typescript
function gcd(a: number, b: number): number {
    if (b === 0) return a;
    return gcd(b, a % b);
}
```

### 5. Checking if a Number is a Power of Two
```typescript
function isPowerOfTwo(n: number): boolean {
    return n > 0 && (n & (n - 1)) === 0;
}
```

### 6. Integer Square Root
```typescript
function integerSquareRoot(k: number): number {
    let low = 0;
    let high = k;
    while (low <= high) {
        let mid = Math.floor((low + high) / 2);
        if (mid * mid <= k) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }
    return low - 1;
}
```

### 7. Searching in a Sparse Array
```typescript
function findInSparseArray(sparseArray: (number | null)[], target: number): number {
    let low = 0;
    let high = sparseArray.length - 1;

    while (low <= high) {
        let mid = Math.floor((low + high) / 2);
        if (sparseArray[mid] === null) {
            let left = mid - 1;
            let right = mid + 1;
            while (true) {
                if (left < low && right > high) return -1;
                if (left >= low && sparseArray[left] !== null) {
                    mid = left;
                    break;
                }
                if (right <= high && sparseArray[right] !== null) {
                    mid = right;
                    break;
                }
                left--;
                right++;
            }
        }
        if (sparseArray[mid] === target) {
            return mid;
        } else if (sparseArray[mid]! < target) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }
    return -1;
}
```

### 8. Exponential Search
```typescript
function exponentialSearch(arr: number[], target: number): number {
    if (arr[0] === target) return 0;
    let i = 1;
    while (i < arr.length && arr[i] <= target) {
        i *= 2;
    }
    return binarySearch(arr, target, i / 2, Math.min(i, arr.length - 1));
}
```

### 9. Finding an Element in a Rotated Sorted Array
```typescript
function searchRotatedArray(arr: number[], target: number): number {
    let low = 0;
    let high = arr.length - 1;

    while (low <= high) {
        let mid = Math.floor((low + high) / 2);
        if (arr[mid] === target) return mid;

        if (arr[low] <= arr[mid]) {
            if (target >= arr[low

] && target < arr[mid]) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        } else {
            if (target > arr[mid] && target <= arr[high]) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
    }
    return -1;
}
```

### 10. Jump Search
```typescript
function jumpSearch(arr: number[], target: number): number {
    let n = arr.length;
    let step = Math.floor(Math.sqrt(n));
    let prev = 0;

    while (arr[Math.min(step, n) - 1] < target) {
        prev = step;
        step += Math.floor(Math.sqrt(n));
        if (prev >= n) return -1;
    }

    while (arr[prev] < target) {
        prev++;
        if (prev === Math.min(step, n)) return -1;
    }

    if (arr[prev] === target) return prev;
    return -1;
}
```

These examples demonstrate algorithms with logarithmic complexity, where the problem size is effectively cut down in each step, leading to significantly reduced processing time as the input size grows.
