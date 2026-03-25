# Core Algorithms (Linear Scope)

## Linear Search
- **Definition:** Sequentially checks each element until target is found.
- **Time Complexity:** O(n).
- **Use Case:** Small datasets, unsorted collections.

---

## Binary Search
- **Definition:** Repeatedly divides sorted array to find target.
- **Precondition:** Input must be sorted.
- **Time Complexity:** O(log n).
- **Use Case:** Large sorted datasets.

---

## Iteration vs Recursion
- **Iteration:** Repetition using loops (for, while).
  - Pros: Lower memory usage.
  - Cons: Sometimes less intuitive.
- **Recursion:** Function calls itself until base case.
  - Pros: Elegant, natural for tree/graph problems.
  - Cons: Higher memory usage (stack frames).

**Comparison:**
- Iteration → Efficient for linear problems.
- Recursion → Simplifies divide-and-conquer problems (e.g., Binary Search, DFS).
