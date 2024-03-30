Focusing on clarity and conciseness while maintaining the accuracy of the information:

---

### Common Time Complexities

#### Constant - O(1)
- Execution time is independent of input size.

#### Linear - O(n)
- Execution time grows linearly with input size.

#### Quadratic - O(n²)
- Often seen in nested loops.

#### Logarithmic - O(log n)
- Each step halves the input size, leading to a slower increase in runtime with larger inputs.

#### Exponential - O(2^n)
- The execution time doubles with each additional input element. E.g., if 5 items take 30 seconds, 6 items will take 60 seconds.

### Data Structures

#### Stack (LIFO)
- **Operations:** 
  - Push (Insertion): O(1)
  - Pop (Deletion): O(1)
  - Get/Search: O(n)
- Efficient for push/pop but not for get/search.

#### Queue (FIFO)
- **Operations:**
  - Enqueue (Insertion): O(1)
  - Dequeue (Deletion): O(n)
  - Get/Search: O(n)

#### Linked List
- **Operations:**
  - Get/Search/Insertion/Deletion: O(n)
- Types include single and doubly linked lists.

#### Binary Search Tree
- **Properties:**
  - Ordered: Left child < Parent < Right child
- **Operations:**
  - Get/Search/Insertion/Deletion: Average O(log n), Worst O(n)
- Involves recursive sub-tree comparisons.

#### Hash Table
- Key-value storage with efficient data access.
- **Operations:**
  - Search/Insertion/Deletion: Average O(1), Worst O(n)

#### Graph
- Comprised of vertices (nodes) and edges (connections).
- Traversal: Depth-First (uses stack), Breadth-First (uses queue).
- Representation: Adjacency Matrix.

### Binary Tree Traversal
- Pre-order: Root, Left, Right
- In-order: Left, Root, Right
- Post-order: Left, Right, Root

### Sorting Algorithms

#### Bubble Sort
- Repeatedly swaps adjacent elements if they are in the wrong order.

#### Insertion Sort
- Inserts elements into their correct position within a sorted subsection of the array.

#### Merge Sort
- Divides the array into halves, sorts each half, and merges them.

#### Quick Sort
- Selects a pivot element and partitions the array around the pivot.

#### Selection Sort
- Repeatedly selects the minimum element and places it at the beginning.

#### Counting Sort
- Counts the occurrences of each element and organizes them accordingly.

#### Bucket Sort
- Distributes elements into buckets, sorts these buckets, and then concatenates them.

#### Radix Sort
- Sorts numbers digit by digit, starting from the least significant digit.

#### Heap Sort
- Creates a heap and repeatedly extracts the maximum element.

---

This optimized content provides a clear, concise overview of common time complexities and data structures, including their operations and traversal methods, as well as a summary of various sorting algorithms.
