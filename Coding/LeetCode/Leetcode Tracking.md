---
tags: [leetcode, programming, algorithms, data-structures]
created: 2024-01-01
updated: 2025-06-27
total_problems: 67
status: active
---

# 🧮 LeetCode Problem Tracker

## 📊 Progress Summary

- **Total Problems Solved**: 67
- **Easy**: 21 problems
- **Medium**: 45 problems
- **Hard**: 1 problem

### 📈 By Topic Distribution

- **Binary Search**: 3 problems
- **Sliding Window**: 7 problems
- **Tree Problems**: 10 problems
- **Heap**: 4 problems
- **Backtracking**: 6 problems
- **Graph**: 6 problems
- **Array & Hashing**: 8 problems
- **Two Pointers**: 10 problems
- **Greedy**: 4 problems
- **Stack**: 3 problems
- **Other**: 5 problems

---

## 🗂️ Problems by Category

### 🔍 [[Binary Search/Binary Search Problems|Binary Search]] (3 problems)

Binary search algorithms and variations including rotated arrays and optimization problems.

### 🪟 [[Sliding Window/Sliding Window Problems|Sliding Window]] (7 problems)

Fixed and dynamic sliding window techniques for substring and subarray problems.

### 🌳 [[Tree/Tree Problems|Tree Problems]] (10 problems)

Binary trees, binary search trees, DFS, BFS, and tree traversal algorithms.

### 🗂️ [[Heap/Heap Problems|Heap]] (4 problems)

Priority queue problems using min-heap and max-heap data structures.

### 🔄 [[Backtracking/Backtracking Problems|Backtracking]] (6 problems)

Recursive backtracking for generating combinations, permutations, and solving constraint satisfaction problems.

### 🕸️ [[Graph/Graph Problems|Graph Problems]] (6 problems)

Graph traversal, cycle detection, and pathfinding using DFS and BFS.

### 🏷️ [[Array & Hashing/Array & Hashing Problems|Array & Hashing]] (8 problems)

Array manipulation and hash table problems for efficient lookups and counting.

### ↔️ [[Two Pointers/Two Pointers Problems|Two Pointers]] (10 problems)

Two-pointer technique for array and string problems, including palindromes and sorted arrays.

### 💰 [[Greedy/Greedy Problems|Greedy]] (4 problems)

Greedy algorithms for optimization problems including jump games and maximum subarray.

### 📚 [[Stack/Stack Problems|Stack]] (3 problems)

Stack-based problems including parentheses validation and expression evaluation.

### 🔧 [[Other/Other Problems|Other]] (5 problems)

Miscellaneous problems that don't fit into the main categories above.

---

# 📚 Algorithm Reference Guide

## 🔍 Binary Search Patterns

### When to use `l <= r` vs `l < r`

**`l <= r`** - Use for finding exact values:

- Continuously searches while there's at least one element to check
- Checks the element when `l == r`
- Used for finding specific values or problems that might return "Not found"
- When you need to examine every possibility

**`l < r`** - Use for finding boundaries/positions:

- Stops when pointers meet, doesn't check when `l == r`
- Used for finding first/last occurrences, insertion positions
- Problems where answers always exist

---

## 🗂️ Heap Operations

### Properties

- **Min-heap**: Each node ≤ its children, smallest at root (index 0)
- **Complete Binary Tree**: All levels filled except possibly last (left to right)
- **Array representation**:
  - Root: index 0
  - Node at index `i`: Left child = `2*i + 1`, Right child = `2*i + 2`, Parent = `(i-1)//2`

### Core Implementation

```python
def heapify(heap):
    """Convert list to heap (bottom-up)"""
    n = len(heap)
    for i in range(n // 2 - 1, -1, -1):
        heapify_down(heap, i)

def heapify_down(heap, index):
    """Move node down until heap property restored"""
    n = len(heap)
    while True:
        left = 2 * index + 1
        right = 2 * index + 2
        smallest = index

        if left < n and heap[left] < heap[smallest]:
            smallest = left
        if right < n and heap[right] < heap[smallest]:
            smallest = right

        if smallest != index:
            heap[index], heap[smallest] = heap[smallest], heap[index]
            index = smallest
        else:
            break

def heapify_up(heap, index):
    """Move node up until heap property restored"""
    while index > 0:
        parent = (index - 1) // 2
        if heap[index] < heap[parent]:
            heap[index], heap[parent] = heap[parent], heap[index]
            index = parent
        else:
            break
```

---

## 🔄 Backtracking Template

```python
def backtrack():
    if base_case:
        # Save solution
        return

    for choice in choices:
        # Make choice
        make_move(choice)

        # Recurse
        backtrack()

        # Unmake choice (backtrack)
        undo_move(choice)
```

**Key principles:**

1. **Make** a choice
2. **Recurse** with that choice
3. **Undo** the choice (restore state)

---

## 🕸️ Graph Algorithms

### Building Adjacency List

```python
from collections import defaultdict

def build_graph(edges):
    graph = defaultdict(list)
    for u, v in edges:
        graph[u].append(v)
        graph[v].append(u)  # For undirected graphs
    return graph

# Example: edges = [[0,1],[1,2],[2,0]]
# Result: {0: [1, 2], 1: [0, 2], 2: [1, 0]}
```

### DFS vs BFS

- **DFS**: Uses stack (recursive/iterative), good for path finding, cycle detection
- **BFS**: Uses queue, good for shortest path in unweighted graphs, level-by-level traversal
- **Always use a visited set** to avoid infinite loops

---

## 💡 Quick Reference

### Common Time Complexities

- **Binary Search**: O(log n)
- **Heap operations**: O(log n) insert/delete, O(1) peek
- **DFS/BFS**: O(V + E) where V = vertices, E = edges
- **Sliding Window**: O(n) for most problems

### Space Optimization Tips

- Use two pointers instead of extra arrays when possible
- Modify input in-place if allowed
- Use bit manipulation for subset problems when applicable

### Debugging Tips

- Draw out small examples
- Check edge cases: empty input, single element, duplicates
- Verify loop conditions and off-by-one errors
- Use print statements to trace algorithm flow

---

## 🎯 Next Steps

### Areas to Focus On

- [ ] **Dynamic Programming** - Major gap in current coverage
- [ ] **Linked Lists** - Missing from current problems
- [ ] **Bit Manipulation** - Useful for optimization
- [ ] **Advanced Graph Algorithms** - Dijkstra, Union-Find
- [ ] **String Algorithms** - KMP, Rabin-Karp
- [ ] **Hard Problems** - Only 1 solved so far

### Recommended Problem Sets

- **NeetCode 150**: Systematic coverage of all patterns
- **LeetCode Top Interview Questions**: Company-focused problems
- **Blind 75**: Essential problems for interviews

---

_Last updated: 2025-06-27_
