# Linearithmic time O(n log n)

Combine a linear aspect with a logarithmic aspect, typically in divide-and-conquer strategies. One of the most common scenarios where you encounter O(n log n) time complexity is in sorting algorithms. Below are some examples in TypeScript, primarily focusing on various sorting algorithms, each explained in detail.

### 1. Merge Sort
Merge sort is a classic example of a divide-and-conquer algorithm with O(n log n) complexity. It divides the array into halves, sorts each half, and then merges them.

```typescript
function mergeSort(arr: number[]): number[] {
    if (arr.length <= 1) return arr; // Base case for recursion

    const middle = Math.floor(arr.length / 2); // Find the middle index
    const left = arr.slice(0, middle); // Divide the array into left half
    const right = arr.slice(middle); // Divide the array into right half

    return merge(mergeSort(left), mergeSort(right)); // Recursively sort and merge
}

function merge(left: number[], right: number[]): number[] {
    let result = []; // Array to store the sorted elements
    let leftIndex = 0, rightIndex = 0;

    // Merge the left and right arrays
    while (leftIndex < left.length && rightIndex < right.length) {
        if (left[leftIndex] < right[rightIndex]) {
            result.push(left[leftIndex++]); // Push the smaller element and increment index
        } else {
            result.push(right[rightIndex++]);
        }
    }

    // Concatenate the remaining elements
    return result.concat(left.slice(leftIndex)).concat(right.slice(rightIndex));
}
```

### 2. Quick Sort
Quick Sort is another divide-and-conquer algorithm with O(n log n) complexity. It selects a 'pivot' element and partitions the array around this pivot.

```typescript
function quickSort(arr: number[], left = 0, right = arr.length - 1): number[] {
    if (left < right) {
        const pivotIndex = partition(arr, left, right); // Get the pivot index
        quickSort(arr, left, pivotIndex - 1); // Recursively sort the left part
        quickSort(arr, pivotIndex + 1, right); // Recursively sort the right part
    }
    return arr;
}

function partition(arr: number[], left: number, right: number): number {
    const pivot = arr[right]; // Choosing the last element as pivot
    let i = left - 1; // Pointer for the greater element

    // Rearrange array by comparing with the pivot
    for (let j = left; j < right; j++) {
        if (arr[j] < pivot) {
            i++;
            [arr[i], arr[j]] = [arr[j], arr[i]]; // Swap elements
        }
    }

    // Swap the pivot element to the correct position
    [arr[i + 1], arr[right]] = [arr[right], arr[i + 1]];
    return i + 1; // Return pivot index
}
```

### 3. Heap Sort
Heap Sort creates a heap from the given data and then sorts it. This algorithm also has O(n log n) complexity.

```typescript
function heapSort(arr: number[]): number[] {
    let n = arr.length;

    // Build max heap
    for (let i = Math.floor(n / 2) - 1; i >= 0; i--) {
        heapify(arr, n, i);
    }

    // Extract elements from the heap
    for (let i = n - 1; i > 0; i--) {
        // Move current root to end
        [arr[0], arr[i]] = [arr[i], arr[0]];
        // call max heapify on the reduced heap
        heapify(arr, i, 0);
    }

    return arr;
}

function heapify(arr: number[], n: number, i: number) {
    let largest = i; // Initialize largest as root
    let left = 2 * i + 1; // left child
    let right = 2 * i + 2; // right child

    // If left child is larger than root
    if (left < n && arr[left] > arr[largest]) largest = left;

    // If right child is larger than largest so far
    if (right < n && arr[right] > arr[largest]) largest = right;

    // If largest is not root
    if (largest !== i) {
        [arr[i], arr[largest]] = [arr[largest], arr[i]]; // Swap
        heapify(arr, n, largest); // Recursively heapify the affected sub-tree
    }
}
```

### 4. Shell Sort


Shell Sort is a variation of insertion sort with a broader scope, leading to an O(n log n) complexity under certain conditions.

```typescript
function shellSort(arr: number[]): number[] {
    let n = arr.length;
    // Start with a big gap and reduce the gap
    for (let gap = Math.floor(n / 2); gap > 0; gap = Math.floor(gap / 2)) {
        // Do a gapped insertion sort for this gap size.
        for (let i = gap; i < n; i += 1) {
            let temp = arr[i]; // store current element
            let j;
            // Shift earlier gap-sorted elements up until the correct location for arr[i] is found
            for (j = i; j >= gap && arr[j - gap] > temp; j -= gap) {
                arr[j] = arr[j - gap];
            }
            arr[j] = temp; // put temp (the original arr[i]) in its correct location
        }
    }
    return arr;
}
```

### 5. Tim Sort
Tim Sort is a hybrid sorting algorithm, derived from merge sort and insertion sort, designed to perform well on many kinds of real-world data. It has O(n log n) complexity.

```typescript
const RUN = 32; // Size of Insertion sort subarray

function timSort(arr: number[]): number[] {
    let n = arr.length;
    // Sort individual subarrays of size RUN
    for (let i = 0; i < n; i += RUN) {
        insertionSort(arr, i, Math.min((i + 31), (n - 1)));
    }

    // Merge sorted subarrays
    for (let size = RUN; size < n; size = 2 * size) {
        for (let left = 0; left < n; left += 2 * size) {
            let mid = left + size - 1;
            let right = Math.min((left + 2 * size - 1), (n - 1));

            if (mid < right) {
                merge(arr, left, mid, right);
            }
        }
    }
    return arr;
}

function insertionSort(arr: number[], left: number, right: number) {
    for (let i = left + 1; i <= right; i++) {
        let temp = arr[i];
        let j = i - 1;
        while (j >= left && arr[j] > temp) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = temp;
    }
}

function merge(arr: number[], l: number, m: number, r: number) {
    let len1 = m - l + 1, len2 = r - m;
    let left = new Array(len1);
    let right = new Array(len2);

    for (let x = 0; x < len1; x++) left[x] = arr[l + x];
    for (let x = 0; x < len2; x++) right[x] = arr[m + 1 + x];

    let i = 0;
    let j = 0;
    let k = l;

    while (i < len1 && j < len2) {
        if (left[i] <= right[j]) {
            arr[k] = left[i];
            i++;
        } else {
            arr[k] = right[j];
            j++;
        }
        k++;
    }

    // Copy remaining elements
    while (i < len1) {
        arr[k] = left[i];
        k++;
        i++;
    }
    while (j < len2) {
        arr[k] = right[j];
        k++;
        j++;
    }
}
```

### 6. Tree Sort
Tree Sort constructs a binary search tree from the given elements and then performs an in-order traversal to get the sorted order. This algorithm also has an average complexity of O(n log n).

```typescript
class TreeNode {
    value: number;
    left: TreeNode | null = null;
    right: TreeNode | null = null;

    constructor(value: number) {
        this.value = value;
    }
}

function treeSort(arr: number[]): number[] {
    if (arr.length === 0) return [];

    let root = new TreeNode(arr[0]); // First element as root

    // Insert remaining elements
    for (let i = 1; i < arr.length; i++) {
        insertNode(root, arr[i]);
    }

    // Store in-order traversal
    let sortedArr: number[] = [];
    inOrderTraversal(root, sortedArr);
    return sortedArr;
}

function insertNode(root: TreeNode, value: number) {
    if (value < root.value) {
        if (root.left === null) root.left

 = new TreeNode(value);
        else insertNode(root.left, value);
    } else {
        if (root.right === null) root.right = new TreeNode(value);
        else insertNode(root.right, value);
    }
}

function inOrderTraversal(node: TreeNode | null, arr: number[]) {
    if (node !== null) {
        inOrderTraversal(node.left, arr);
        arr.push(node.value);
        inOrderTraversal(node.right, arr);
    }
}
```

### 7. Intro Sort
Intro Sort is a hybrid sorting algorithm that begins with quick sort and switches to heap sort when the recursion depth exceeds a level based on the number of elements being sorted.

```typescript
function introSort(arr: number[], depthLimit: number = Math.floor(Math.log(arr.length) * 2)): number[] {
    let n = arr.length;
    introSortHelper(arr, 0, n - 1, depthLimit);
    return arr;
}

function introSortHelper(arr: number[], start: number, end: number, depthLimit: number) {
    let n = end - start + 1;
    if (n <= 1) return;

    if (depthLimit === 0) {
        // Perform heap sort
        heapSort(arr);
        return;
    }

    if (start < end) {
        let pivotIndex = partition(arr, start, end);
        introSortHelper(arr, start, pivotIndex - 1, depthLimit - 1);
        introSortHelper(arr, pivotIndex + 1, end, depthLimit - 1);
    }
}

// Reusing the partition and heapify functions from earlier examples
```

### 8. Ternary Quick Sort
This is a variation of quicksort that divides the array into three parts, based on two pivots. It's particularly effective for arrays with many duplicate elements.

```typescript
function ternaryQuickSort(arr: number[], low = 0, high = arr.length - 1): number[] {
    if (low < high) {
        let [mid1, mid2] = ternaryPartition(arr, low, high);
        ternaryQuickSort(arr, low, mid1 - 1);
        ternaryQuickSort(arr, mid1 + 1, mid2 - 1);
        ternaryQuickSort(arr, mid2 + 1, high);
    }
    return arr;
}

function ternaryPartition(arr: number[], low: number, high: number): [number, number] {
    if (arr[high] < arr[low])
        [arr[low], arr[high]] = [arr[high], arr[low]];

    let pivot1 = arr[low], pivot2 = arr[high];
    let i = low + 1, j = high - 1, k = low + 1;

    while (k <= j) {
        if (arr[k] < pivot1) {
            [arr[k], arr[i]] = [arr[i], arr[k]];
            i++;
        } else if (arr[k] > pivot2) {
            [arr[k], arr[j]] = [arr[j], arr[k]];
            j--;
            k--; // Stay in place to check new element
        }
        k++;
    }
    i--; j++;
    [arr[low], arr[i]] = [arr[i], arr[low]];
    [arr[high], arr[j]] = [arr[j], arr[high]];
    return [i, j]; // Return the indices of the pivots
}
```

### 9. Balanced Quick Sort
This version of quicksort attempts to balance the partitions to avoid worst-case scenarios.

```typescript
function balancedQuickSort(arr: number[], left = 0, right = arr.length - 1): number[] {
    if (left < right) {
        let pivotIndex = balancedPartition(arr, left, right);
        balancedQuickSort(arr, left, pivotIndex - 1);
        balancedQuickSort(arr, pivotIndex + 1, right);
    }
    return arr;
}

function balancedPartition(arr: number[], left: number, right: number): number {
    let pivot = arr[Math.floor((left + right) / 2)]; // Choose middle element as pivot
    let i = left, j = right;

    while (i <= j) {
        while (arr[i] < pivot) i++;
        while (arr[j] > pivot) j--;

        if (i <= j) {
            [arr[i], arr[j]] = [arr[j], arr[i]];
            i++; j--;
        }
    }
    return i;
}
```

### 10. Strand Sort
Strand sort is a stable sorting algorithm that is useful for linked lists. It repeatedly pulls sorted subsequences from the list and merges them.

```typescript
function strandSort(arr: number[]): number[] {
    let result: number[] = [];
    while (arr

.length) {
        let sublist: number[] = [arr.shift() as number]; // Initialize sublist with the first element
        for (let i = 0; i < arr.length; i++) {
            if (arr[i] >= sublist[sublist.length - 1]) {
                sublist.push(arr.splice(i--, 1)[0]); // Append to sublist and remove from arr
            }
        }
        result = merge(result, sublist); // Merge sublist into the result
    }
    return result;
}

// Reusing the merge function from merge sort example
```

In these examples, the O(n log n) complexity mainly comes from the repeated division of the problem (usually in half) and then linearly solving or combining these parts. This characteristic is common in efficient sorting algorithms and certain divide-and-conquer strategies.
