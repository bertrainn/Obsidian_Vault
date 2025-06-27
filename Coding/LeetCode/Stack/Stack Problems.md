---
tags: [leetcode, stack, algorithms]
created: 2025-06-27
updated: 2025-06-27
total_problems: 3
difficulty_breakdown:
  easy: 1
  medium: 2
  hard: 0
---

# 📚 Stack Problems

## 📊 Summary

- **Total Problems**: 3
- **Difficulty**: 1 Easy, 2 Medium

---

## Problems

| #   | Problem Name                                                                                        | Difficulty | Algorithm Used   | Optimal Solution                                                                                                                                                                                                                                                                           |
| --- | --------------------------------------------------------------------------------------------------- | ---------- | ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 20  | [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)                               | Easy       | Stack            | - if it's an open char we want to append<br>- if we add a close char to the empty stack we just return False cause it's not valid<br>- close char we want to check the top of the stack<br>- if it's not a matching opening char -> return false<br>- if it is we gucci and we just pop it |
| 150 | [Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/) | Medium     | Stack            | - iterate through the array<br>- check for value<br>- value is alpha => add to the stack<br>- value is not alpha do the operation:<br>- append result to the stack                                                                                                                         |
| 22  | [Generate Parentheses](https://leetcode.com/problems/generate-parentheses/)                         | Medium     | Stack/ Backtrack | - using backtrack<br>- keep track of the open and closed<br>- just add and pop accordingly                                                                                                                                                                                                 |

---

_Back to [[Leetcode Tracking]]_
