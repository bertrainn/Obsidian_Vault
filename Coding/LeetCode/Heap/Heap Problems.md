---
tags: [leetcode, heap, priority-queue, algorithms]
created: 2025-06-27
updated: 2025-06-27
total_problems: 4
difficulty_breakdown:
  easy: 1
  medium: 3
  hard: 0
---

# 🗂️ Heap Problems

## 📊 Summary

- **Total Problems**: 4
- **Difficulty**: 1 Easy, 3 Medium

---

## Problems

| #    | Problem Name                                                                                      | Difficulty | Algorithm Used | Optimal Solution                                                                                                                                                                                                                                    |
| ---- | ------------------------------------------------------------------------------------------------- | ---------- | -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1046 | [Last Stone Weight](https://leetcode.com/problems/last-stone-weight/)                             | Easy       | Heap           | - Convert all elements to negative<br>- Call heapify -> make it into a max heap<br>- pop the top 2 elements<br>- find the diff<br>- add the diff back to the heap if > 0<br>- continue until list only has 1 element                                |
| 215  | [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/) | Medium     | Heap           | - Min heap -> keep adding elements to the min heap, if the len is more than K, push the element than pop. (heappushpop())<br>- Max heap -> pop the heap K - 1 times, and return the element (longer time complexity due to setting up the max heap) |
| 347  | [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)                 | Medium     | Heap           | - Min Heap and Counter (dictionary)<br>- bruh it's the same as the previous lmao <br>- It works cause python will do a comparison based on the first element in the tuple (value, key)                                                              |
| 973  | [K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/)           | Medium     | Heap           | - Max heap<br>- It do be the same<br>- Just rmb to negate the euclidian distance to maintain the max_heap                                                                                                                                           |

---

## Notes

### Heap Properties

- **Min-heap**: The value of each node is less than or equal to the value of its children. The smallest element is always at the root (index 0)
- **Complete BT**: Heaps are typically implemented using arrays, representing a complete Binary Tree.
  - Complete BT is one where all levels are filled except possibly the last level, which is filled from left to right

### Array Representation

- Root: index 0
- For a node at index i:
  - Left child: 2 \* i + 1
  - Right child: 2 \* i + 2
  - Parent: (i - 1) // 2

### Important Code

#### Heapify

```python
"""
Converts a list into a heap in-place (bottom-up approach)
"""
heap = []

def heapify(heap):
	n = len(heap)
	for i in range(n // 2 - 1, -1, -1):
		heapify_down(i)

"""
Move a node down the tree until the heap property is restored
"""
def heapify_down(heap, index):
	n = len(heap)
	while True:
		left_child_index = 2 * index + 1
		right_child_index = 2 * index + 2
		smallest = index #assume current node is the smallest

	if left_child_index < n and heap[left_child_index] < heap[smallest]:
		smallest = left_child_index

	if right_child_index < n and heap[right_child_index] < heap[smallest]:
		smallest = right_child_index

	if smallest != index:
		# Swap the current node with the smallest child
		heap[index], heap[smallest] = heap[smallest], heap[index]
		index = smallest
	else:
		break # Heap Property is statisfied

"""
Move a node up the tree until the heap property is restored
"""
def heapify_up(heap, index):
	while index > 0:
		parent_index = (index - 1) // 2
		if heap[index] < heap[parent_index]:
			heap[index], heap[parent_index] = heap[parent_index], heap[index]
			index = parent_index
		else:
			break
```

---

_Back to [[Leetcode Tracking]]_
