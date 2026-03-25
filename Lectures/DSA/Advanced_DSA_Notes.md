# Advanced DSA Notes

---

## Hash-based DS & Algorithms

### Set / Map as ADT
- **Set**: Stores unique elements, no duplicates allowed.
- **Map**: Stores key-value pairs, keys must be unique.
- Common operations: insert, delete, search, lookup.

### Hash Table & Collision
- **Hash Table**: Uses a hash function to map keys to indices in an array.
- **Collision**: Occurs when two keys map to the same index.
- Collision resolution techniques:
  - **Chaining**: Store multiple elements at the same index using linked lists.
  - **Open Addressing**: Probe for the next available slot (linear, quadratic, double hashing).

### Frequency Counting
- Use hash maps to count occurrences of elements efficiently.
- Example: Counting word frequency in a text document.
- Time complexity: **O(n)** for n elements.

### Deduplication
- Use sets to remove duplicates from a collection.
- Example: Removing duplicate email addresses from a list.
- Efficient for large datasets.

---

## Sorting Algorithms

### Why Sorting Matters
- Sorting improves efficiency of searching and data organization.
- Used in databases, analytics, and optimization problems.
- Many algorithms rely on sorted data for efficiency.

### Bubble Sort (Concept)
- Repeatedly swap adjacent elements if they are in the wrong order.
- Simple but inefficient.
- Time complexity: **O(n²)** in worst and average cases.

### Merge Sort
- **Divide and Conquer** algorithm.
- Splits array into halves, sorts recursively, and merges.
- Time complexity: **O(n log n)**.
- Stable sorting algorithm.

### Quick Sort (Idea)
- Select a pivot, partition array around pivot, recursively sort partitions.
- Average case: **O(n log n)**.
- Worst case: **O(n²)** (if pivot selection is poor).
- Generally faster than Merge Sort in practice.

### Stable vs Unstable Sorting
- **Stable**: Preserves relative order of equal elements (e.g., Merge Sort).
- **Unstable**: May change order of equal elements (e.g., Quick Sort).

---

## Tree & Heap

### Tree / BST / Balanced BST (Concept)
- **Tree**: Hierarchical structure with nodes.
- **Binary Search Tree (BST)**: Left child < parent < right child.
- **Balanced BST** (AVL, Red-Black Trees): Ensures logarithmic height for efficient operations.

### Tree Traversal
- **Inorder**: Left → Root → Right.
- **Preorder**: Root → Left → Right.
- **Postorder**: Left → Right → Root.
- Applications: expression evaluation, searching, hierarchical data.

### Heap & Priority Queue
- **Heap**: Complete binary tree with heap property.
  - Max-Heap: Parent ≥ children.
  - Min-Heap: Parent ≤ children.
- **Priority Queue**: Abstract data type implemented using heaps.
  - Operations: insert, extract-max/min.

### Top-K Use Cases
- Use heaps to efficiently find top-K largest or smallest elements.
- Applications:
  - Leaderboards.
  - Search engines (top results).
  - Recommendation systems.

---
