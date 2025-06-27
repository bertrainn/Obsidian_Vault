---
tags: [leetcode, tree, binary-tree, bst, algorithms]
created: 2025-06-27
updated: 2025-06-27
total_problems: 10
difficulty_breakdown:
  easy: 7
  medium: 3
  hard: 0
---

# 🌳 Tree Problems

## 📊 Summary

- **Total Problems**: 10
- **Difficulty**: 7 Easy, 3 Medium

---

## Problems

| #   | Problem Name                                                                                                                    | Difficulty | Algorithm Used                     | Optimal Solution                                                                                                                                                                                                                                                                |
| --- | ------------------------------------------------------------------------------------------------------------------------------- | ---------- | ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 226 | [Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/)                                                         | Easy       | Tree (Binary Tree) DFS             | - do DFS on the root of the tree<br>- swap the left and right nodes<br>- Then DFS on left then right<br>- Return the root of the tree                                                                                                                                           |
| 104 | [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)                                     | Easy       | Tree (Binary) DFS                  | - Do DFS <br>- Return 1 + max(DFS(root left, root right))                                                                                                                                                                                                                       |
| 110 | [Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/)                                                     | Easy       | Tree (Binary) DFS                  | - Create a global Balanced variable to keep track of the whole tree<br>- do a "maximum depth" on left and right side to find the height of each branch<br>- check if the abs(left - right) > 1, if it is update the global balance                                              |
| 543 | [Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/)                                               | Easy       | Tree (Binary) DFS                  | - Keep a global max diameter viable<br>- Better to think of "building" the diameter from the bottom up -> basically cal the diameter for every node <br>- cal the left and right diameter<br>- update the max                                                                   |
| 100 | [Same Tree](https://leetcode.com/problems/same-tree/)                                                                           | Easy       | Tree (Binary) DFS                  | - Do DFS <br>- Compare the t1.val and t2.val <br>- Then compare the left and right nodes                                                                                                                                                                                        |
| 101 | [Symmetric Tree](https://leetcode.com/problems/symmetric-tree/)                                                                 | Easy       | Tree (Binary) DFS                  | - DFS<br>- Imagine having 2 pointers which iterate through the Tree<br>- Similar to "Same Tree"                                                                                                                                                                                 |
| 112 | [Path Sum](https://leetcode.com/problems/path-sum/)                                                                             | Easy       | Tree (Binary) DFS                  | - DFS <br>- Keep a running total (doing decremental iterations don't account for a empty list with target 0)<br>- check if the target == cur if it is the last node (i.e. no left and right child)                                                                              |
| 572 | [Subtree of Another Tree](https://leetcode.com/problems/subtree-of-another-tree/)                                               | Medium     | Tree (Binary)<br>DFS               | - Use "Same Tree"<br>- Run the same tree logic on every single node and see when it returns true                                                                                                                                                                                |
| 102 | [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)                           | Medium     | Tree (Binary)<br>BFS               | - Conduct a BFS on the tree. -> use a Queue<br>- Using a for loop as you add to the list                                                                                                                                                                                        |
| 203 | [Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)                                   | Medium     | Tree (BST)<br>In Order Transversal | - In order (LNR) transversal of a BST = Numerical order <br>- keep track of a global count and answer var<br>- Do inorder on the BST<br>- Decrementing the count, when the count hits 1 -> number has been found <br>- Update the values<br>                                    |
| 503 | [Minimum Absolute Difference in BST](https://leetcode.com/problems/minimum-absolute-difference-in-bst/)                         | Easy       | Tree (BST)<br>In Order             | - Basically, Inorder goes through the list numerically, so just keep track of the previous element and update the global values accordingly                                                                                                                                     |
| 98  | [Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)                                       | Medium     | Tree (BST)<br>DFS                  | - Each node in a BST must be somewhere inbetween a max and min value                                                                                                                                                                                                            |
| 235 | [Lowest Common Ancestor of a Binary Search Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/) | Medium     | Tree(BST)<br>                      | - Similar idea to before. <br>- Keep a running track of the LCA <br>- if current node is q or p -> return we good<br>- if node val < q and p -> node is too small -> go right<br>- if node val > q and p -> node is too big -> go left<br>- else we at the optimal spot alr<br> |

---

_Back to [[Leetcode Tracking]]_
