---
tags: [leetcode, greedy, algorithms]
created: 2025-06-27
updated: 2025-06-27
total_problems: 4
difficulty_breakdown:
  easy: 0
  medium: 4
  hard: 0
---

# 💰 Greedy Problems

## 📊 Summary

- **Total Problems**: 4
- **Difficulty**: 4 Medium

---

## Problems

| #   | Problem Name                                                        | Difficulty | Algorithm Used | Optimal Solution                                                                                                                                                                                                                                                                         |
| --- | ------------------------------------------------------------------- | ---------- | -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 53  | [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/) | Medium     | Greedy         | -iterate through the list, keeping track of the total<br>- if total < 0: reset it back to 0                                                                                                                                                                                              |
| 55  | [Jump Game](https://leetcode.com/problems/jump-game/)               | Medium     | Greedy         | - start from the end of the array<br>- target = end of the array<br>- check if current index + num[index] >= target<br> - update the target to the current index<br>return if target == 0                                                                                                |
| 45  | [Jump Game II](https://leetcode.com/problems/jump-game-ii/)         | Medium     | Greedy         | - run a pesudo BFS<br>- define a l, r boundary that we can use to split up the array <br>- r being the furthest point that we can jump to given the current situation<br>- l just being r + 1 (from the previous border)<br>- run a for loop from l to r to find the next furthest point |
| 134 | [Gas Station](https://leetcode.com/problems/gas-station/)           | Medium     | Greedy         |                                                                                                                                                                                                                                                                                          |

---

_Back to [[Leetcode Tracking]]_
