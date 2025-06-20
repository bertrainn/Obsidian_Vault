---

---
# 🧮 LeetCode Problem Tracker

| #    | Problem Name                                                                                                                    | Difficulty | Algorithm Used                     | Optimal Solution                                                                                                                                                                                                                                                                                |
| ---- | ------------------------------------------------------------------------------------------------------------------------------- | ---------- | ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 153  | [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)                     | Medium     | Binary Search                      | Binary Search <br>check if the nums[middle] > nums[right], if it is close off l to middle + 1 else r = m<br>                                                                                                                                                                                    |
| 33   | [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)                                 | Medium     | Binary Search                      | - Do a find min in rotated sorted array first to create a partition<br>- Find L, R pointers based on which partition the target is in<br>- Do regular BS within the partition                                                                                                                   |
| 875  | [Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/)                                                       | Medium     | Binary Search                      | - L, R = 1 and max(amount possible), rate = (l + r) // 2<br>- Calc the total hours it takes to eat the piles at that rate.<br>- if total_time_taken <= h -> we too fast can go slower<br>- else total_time_taken > h -> we too slow go faster<br>return r                                       |
| 643  | [Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/)                                         | Easy       | Sliding Window (Fixed size)        | - Build up the current sum (first k ele)<br>- iterate through the remaining ele with the fixed window <br>- cal and update the avg as you go along                                                                                                                                              |
| 1004 | [Max Consecutive Ones III](https://leetcode.com/problems/max-consecutive-ones-iii/)                                             | Medium     | Sliding Window (Dynamic)           | - keep track of max window, zero count<br>- Iterate through the list only caring about 0s -> opening the window<br>- check if 0 count is more than k <br>- if it is increment l (reducing the 0 count if nums\[l] is a 0) -> closing the window<br>- calc the window size and update max window |
| 3    | [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/) | Medium     | Sliding Window (Dyanmic)           | - Use a set to keep track of chars in the substring<br>- iterate through the string<br>- if you encounter a dup, continually pop the left most character until the dup is gone <br>- add the char into the string and cal the substring length                                                  |
| 424  | [Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)               | Medium     | Sliding Window (Dynamic)           | - Use a "map" to keep track of the number of char seen<br>- Keep adding elements into the count -> expand the window<br>- When the (window size) - (highest occurring char) > k -> no more replacements -> start popping from the left                                                          |
| 209  | [Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)                                           | Medium     | Sliding Window                     | - Read the fukin question JFC<br>- Keep adding values -> Opening the window<br>- Only start closing after total_sum >= target -> pop left and update accordingly                                                                                                                                |
| 567  | [Permutation in String](https://leetcode.com/problems/permutation-in-string/)                                                   | Medium     | Sliding Window                     | - keep 2 maps (s1 and s2)<br>- append the char at r -> open window<br>- if the window is bigger than the len of s1 -> close the window <br>- if the 2 arrays == -> return True                                                                                                                  |
| 226  | [Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/)                                                         | Easy       | Tree (Binary Tree) DFS             | - do DFS on the root of the tree<br>- swap the left and right nodes<br>- Then DFS on left then right<br>- Return the root of the tree                                                                                                                                                           |
| 104  | [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)                                     | Easy       | Tree (Binary) DFS                  | - Do DFS <br>- Return 1 + max(DFS(root left, root right))                                                                                                                                                                                                                                       |
| 110  | [Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/)                                                     | Easy       | Tree (Binary) DFS                  | - Create a global Balanced variable to keep track of the whole tree<br>- do a "maximum depth" on left and right side to find the height of each branch<br>- check if the abs(left - right) > 1, if it is update the global balance                                                              |
| 543  | [Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/)                                               | Easy       | Tree (Binary) DFS                  | - Keep a global max diameter viable<br>- Better to think of "building" the diameter from the bottom up -> basically cal the diameter for every node <br>- cal the left and right diameter<br>- update the max                                                                                   |
| 100  | [Same Tree](https://leetcode.com/problems/same-tree/)                                                                           | Easy       | Tree (Binary) DFS                  | - Do DFS <br>- Compare the t1.val and t2.val <br>- Then compare the left and right nodes                                                                                                                                                                                                        |
| 101  | [Symmetric Tree](https://leetcode.com/problems/symmetric-tree/)                                                                 | Easy       | Tree (Binary) DFS                  | - DFS<br>- Imagine having 2 pointers which iterate through the Tree<br>- Similar to "Same Tree"                                                                                                                                                                                                 |
| 112  | [Path Sum](https://leetcode.com/problems/path-sum/)                                                                             | Easy       | Tree (Binary) DFS                  | - DFS <br>- Keep a running total (doing decremental iterations don't account for a empty list with target 0)<br>- check if the target == cur if it is the last node (i.e. no left and right child)                                                                                              |
| 572  | [Subtree of Another Tree](https://leetcode.com/problems/subtree-of-another-tree/)                                               | Medium     | Tree (Binary)<br>DFS               | - Use "Same Tree"<br>- Run the same tree logic on every single node and see when it returns true                                                                                                                                                                                                |
| 102  | [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)                           | Medium     | Tree (Binary)<br>BFS               | - Conduct a BFS on the tree. -> use a Queue<br>- Using a for loop as you add to the list                                                                                                                                                                                                        |
| 203  | [Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)                                   | Medium     | Tree (BST)<br>In Order Transversal | - In order (LNR) transversal of a BST = Numerical order <br>- keep track of a global count and answer var<br>- Do inorder on the BST<br>- Decrementing the count, when the count hits 1 -> number has been found <br>- Update the values<br>                                                    |
| 503  | [Minimum Absolute Difference in BST](https://leetcode.com/problems/minimum-absolute-difference-in-bst/)                         | Easy       | Tree (BST)<br>In Order             | - Basically, Inorder goes through the list numerically, so just keep track of the previous element and update the global values accordingly                                                                                                                                                     |
| 98   | [Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)                                       | Medium     | Tree (BST)<br>DFS                  | - Each node in a BST must be somewhere inbetween a max and min value                                                                                                                                                                                                                            |
| 235  | [Lowest Common Ancestor of a Binary Search Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/) | Medium     | Tree(BST)<br>                      | - Similar idea to before. <br>- Keep a running track of the LCA <br>- if current node is q or p -> return we good<br>- if node val < q and p -> node is too small -> go right<br>- if node val > q and p -> node is too big -> go left<br>- else we at the optimal spot alr<br>                 |
| 1046 | [Last Stone Weight](https://leetcode.com/problems/last-stone-weight/)                                                           | Easy       | Heap                               | - Convert all elements to negative<br>- Call heapify -> make it into a max heap<br>- pop the top 2 elements<br>- find the diff<br>- add the diff back to the heap if > 0<br>- continue until list only has 1 element                                                                            |
| 215  | [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/)                               | Medium     | Heap                               | - Min heap -> keep adding elements to the min heap, if the len is more than K, push the element than pop. (heappushpop())<br>- Max heap -> pop the heap K - 1 times, and return the element (longer time complexity due to setting up the max heap)                                             |
| 347  | [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)                                               | Medium     | Heap                               | - Min Heap and Counter (dictionary)<br>- bruh it's the same as the previous lmao <br>- It works cause python will do a comparison based on the first element in the tuple (value, key)                                                                                                          |
| 973  | [K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/)                                         | Medium     | Heap                               | - Max heap<br>- It do be the same<br>- Just rmb to negate the euclidian distance to maintain the max_heap                                                                                                                                                                                       |
| 78   | [Subsets](https://leetcode.com/problems/subsets/)                                                                               | Medium     | Backtracking                       | - res and solution global variables<br>- define base case (index == len of nums), add copy of solution to res<br>- option A -> don't add value, conduct backtracking<br>- option B -> add value, backtrack, remove said value                                                                   |
| 46   | [Permutations](https://leetcode.com/problems/permutations/)                                                                     | Medium     | Backtracking                       | - res and sol global variables<br>- basecase -> len(sol) == len(nums): append sol to res<br>- go down the path of using a number if it is not in the sol                                                                                                                                        |
| 77   | [Combinations](https://leetcode.com/problems/combinations/)                                                                     | Medium     | Backtracking                       | - res and sol global variables<br>- basecase -> len(sol) == k: append a copy of sol to res<br>- build the combinations from the nth value downwards<br>- way to make is faster is to check if the number of values left > the number of values needed                                           |
|      |                                                                                                                                 |            |                                    |                                                                                                                                                                                                                                                                                                 |


# Random Notes
## Binary Search
l <= r:
-  Continuously searches while there's at least one element to check
- Checks the element when l == r
- used for finding exact values
- Used for
	- Finding specific values
	- Problems that might return **Not found**
	- When you need to examine every possibility 
l < r: 
- Stops when pointers meet
- doesn't check when l == r
- used for finding boundaries/ positions 
- Used for
	- Finding first/ last occurrences 
	- Finding insertion positions 
	- Problems where answers always exists 


## Heaps
* Heap Properties: In a min-heap, the value of each node is less than or equal to the value of its children. The smallest element is always at the root (index 0)
* Complete BT: Heaps are typically implemented using arrays, representing a complete Binary Tree. 
	* Complete BT is one where all levels are filled except possibly the last level, which is filled from left to right
* Array Representation
	* Root: index 0
	* For a node at index i: 
		* Left child: 2 * i + 1
		* Right child: 2 * i + 2
		* Parent: (i - 1) // 2

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

## Backtracking

``` python

def backtracking(): 
	if (some base case):
		some random modification
		return

	backtracking(a) -> take option A

	some modification -> take option B 
	backtracking(b) -> continue with option B
	undo option B


```