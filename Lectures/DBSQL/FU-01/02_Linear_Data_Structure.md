# Linear Data Structures

## 1. Array / Dynamic Array
- **Array:** A fixed-size collection of elements stored in contiguous memory locations.  
  *Key Points:*  
  - Fast access using index (O(1)).  
  - Size is fixed at creation.  
  - Insertion/deletion can be costly (O(n)) due to shifting elements.

- **Dynamic Array (e.g., ArrayList in Java):**  
  - Resizable array that grows/shrinks automatically.  
  - Provides flexibility compared to static arrays.  
  - Amortized insertion at the end is O(1).  

---

## 2. Linked List
- **Definition:** A sequence of nodes where each node contains data and a reference (pointer) to the next node.  
- **Types:**  
  - Singly Linked List (one pointer per node).  
  - Doubly Linked List (two pointers: next and previous).  
- **Advantages:**  
  - Dynamic size.  
  - Efficient insertion/deletion (O(1)) if node reference is known.  
- **Disadvantages:**  
  - Sequential access only (O(n) for search).  
  - Extra memory for pointers.

---

## 3. Stack
- **Definition:** A linear data structure that follows **LIFO (Last In, First Out)** principle.  
- **Operations:**  
  - `push` → Insert element.  
  - `pop` → Remove top element.  
  - `peek` → View top element.  
- **Implementation:** Can be built using arrays or linked lists.  
- **Use Cases:**  
  - Function call management (recursion).  
  - Undo/Redo operations in editors.  
  - Expression evaluation (postfix/prefix).

---

## 4. Queue / Deque
- **Queue:** A linear data structure that follows **FIFO (First In, First Out)** principle.  
  - `enqueue` → Insert element at rear.  
  - `dequeue` → Remove element from front.  
  - Used in scheduling, buffering, and resource management.

- **Deque (Double-Ended Queue):**  
  - Allows insertion and deletion from both ends.  
  - More flexible than a standard queue.  
  - Can be used to implement stacks and queues efficiently.

---

## 5. Use Cases of Linear Data Structures
- **Array / Dynamic Array:**  
  - Storing fixed or resizable collections.  
  - Fast random access (e.g., lookup tables).

- **Linked List:**  
  - Dynamic memory allocation.  
  - Efficient insertions/deletions (e.g., playlist management).

- **Stack:**  
  - Function call stack in programming languages.  
  - Backtracking algorithms (maze solving, DFS).

- **Queue:**  
  - Task scheduling (CPU, printers).  
  - Breadth-First Search (BFS) in graphs.  

- **Deque:**  
  - Sliding window problems.  
  - Implementing both stack and queue operations.

---

## Summary
- **Arrays/Dynamic Arrays:** Best for fast access.  
- **Linked Lists:** Best for frequent insertions/deletions.  
- **Stacks:** Best for LIFO operations.  
- **Queues/Deques:** Best for FIFO and flexible double-ended operations.  
- Choosing the right linear data structure depends on the problem requirements.
