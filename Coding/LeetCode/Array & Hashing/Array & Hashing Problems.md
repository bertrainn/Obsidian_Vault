---
tags: [leetcode, array, hashing, algorithms]
created: 2025-06-27
updated: 2025-06-27
total_problems: 8
difficulty_breakdown:
  easy: 3
  medium: 5
  hard: 0
---

# 🏷️ Array & Hashing Problems

## 📊 Summary

- **Total Problems**: 8
- **Difficulty**: 3 Easy, 5 Medium

---

## Problems

| #   | Problem Name                                                                                | Difficulty | Algorithm Used    | Optimal Solution                                                                                                                                                                          |
| --- | ------------------------------------------------------------------------------------------- | ---------- | ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 217 | [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)                     | Easy       | Array and Hashing | - bruh if i can't do this I should just kms                                                                                                                                               |
| 242 | [Valid Anagram](https://leetcode.com/problems/valid-anagram/)                               | Easy       | Array and Hashing | - Use a hashmap lmao                                                                                                                                                                      |
| 1   | [Two Sum](https://leetcode.com/problems/two-sum/)                                           | Easy       | Hashing           | - use a hashmap <br>- key value pair is {diff value: the index of the value to make the diff}                                                                                             |
| 49  | [Group Anagrams](https://leetcode.com/problems/group-anagrams/)                             | Medium     | Array             | - iterate through the list of strings<br>- iterate through char of strings<br>- convert counter into tuple to act as a key<br>- append the key in the dict <br>return as a list of values |
| 238 | [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/) | Medium     | Array             | - calc the products from going left and right<br>- mult the 2 arrays together<br>- actually just math mambo jumbo                                                                         |
| 36  | [Valid Sudoku](https://leetcode.com/problems/valid-sudoku/)                                 | Medium     | Array             | - have a default dict (set) for Col, Row and square <br>- then just check if said value is in the Row[r], col[c] and square[(r // 3, c // 3)]<br>- then append                            |
| 128 | [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/) | Medium     | Array             | - convert into a set()<br>- iterate with a for num in nums<br>- check if the num - 1 in set<br>- if not -> initate lenght at 1, then start counting                                       |
| 169 | [Majority Element](https://leetcode.com/problems/majority-element/)                         | Easy       | Array             | - keep track of a highest_count<br>- if highest count == 0 assign a new ele<br>- num == ele, highest += 1<br>else -= 1                                                                    |

---

_Back to [[Leetcode Tracking]]_
