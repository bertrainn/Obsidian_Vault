---
tags: [leetcode, sliding-window, algorithms]
created: 2025-06-27
updated: 2025-06-27
total_problems: 7
difficulty_breakdown:
  easy: 2
  medium: 5
  hard: 0
---

# 🪟 Sliding Window Problems

## 📊 Summary

- **Total Problems**: 7
- **Difficulty**: 2 Easy, 5 Medium

---

## Problems

| #    | Problem Name                                                                                                                    | Difficulty | Algorithm Used              | Optimal Solution                                                                                                                                                                                                                                                                                |
| ---- | ------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 643  | [Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/)                                         | Easy       | Sliding Window (Fixed size) | - Build up the current sum (first k ele)<br>- iterate through the remaining ele with the fixed window <br>- cal and update the avg as you go along                                                                                                                                              |
| 1004 | [Max Consecutive Ones III](https://leetcode.com/problems/max-consecutive-ones-iii/)                                             | Medium     | Sliding Window (Dynamic)    | - keep track of max window, zero count<br>- Iterate through the list only caring about 0s -> opening the window<br>- check if 0 count is more than k <br>- if it is increment l (reducing the 0 count if nums\[l] is a 0) -> closing the window<br>- calc the window size and update max window |
| 3    | [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/) | Medium     | Sliding Window (Dyanmic)    | - Use a set to keep track of chars in the substring<br>- iterate through the string<br>- if you encounter a dup, continually pop the left most character until the dup is gone <br>- add the char into the string and cal the substring length                                                  |
| 424  | [Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)               | Medium     | Sliding Window (Dynamic)    | - Use a "map" to keep track of the number of char seen<br>- Keep adding elements into the count -> expand the window<br>- When the (window size) - (highest occurring char) > k -> no more replacements -> start popping from the left                                                          |
| 209  | [Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)                                           | Medium     | Sliding Window              | - Read the fukin question JFC<br>- Keep adding values -> Opening the window<br>- Only start closing after total_sum >= target -> pop left and update accordingly                                                                                                                                |
| 567  | [Permutation in String](https://leetcode.com/problems/permutation-in-string/)                                                   | Medium     | Sliding Window              | - keep 2 maps (s1 and s2)<br>- append the char at r -> open window<br>- if the window is bigger than the len of s1 -> close the window <br>- if the 2 arrays == -> return True                                                                                                                  |
| 219  | [Contains Duplicate II](https://leetcode.com/problems/contains-duplicate-ii/)                                                   | Easy       | Sliding Window              | - use a set() <br>- at the start check if r - l > k -> pop accordingly <br>- check if val in the set<br>- append                                                                                                                                                                                |
| 121  | [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)                               | Easy       | Sliding Window              | - check if price[l] < price[r], calc accordingly<br>- else update l to r                                                                                                                                                                                                                        |


---

_Back to [[Leetcode Tracking]]_
