---
tags: [leetcode, miscellaneous, algorithms]
created: 2025-06-27
updated: 2025-06-27
total_problems: 5
difficulty_breakdown:
  easy: 3
  medium: 2
  hard: 0
---

# 🔧 Other Problems

## 📊 Summary

- **Total Problems**: 5
- **Difficulty**: 3 Easy, 2 Medium

---

## Problems

| #    | Problem Name                                                                    | Difficulty | Algorithm Used | Optimal Solution                                                                                                                                                                                      |
| ---- | ------------------------------------------------------------------------------- | ---------- | -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|      | Encode and Decode Strings                                                       | Medium     | Array          | - encode -> set the encoded string as number+#+string<br>- decode -> use a while loop to iterate and go through the values, can use 2 pointers for this                                               |
| 16   | [3Sum Closest](https://leetcode.com/problems/3sum-closest/)                     | Medium     | Array          | - Basically same as 3sum only diff is just keep track of the current nearest value and calc what the abs diff is and update accordingly                                                               |
| 1929 | [Concatenation of Array](https://leetcode.com/problems/concatenation-of-array/) | Easy       | Array          | aiya just 2 pass this shit                                                                                                                                                                            |
| 14   | [Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/)   | Easy       | Array          | - first find the length of the smallest word <br>- for each letter at index just check if it matches through all the words <br>- if it does increment i<br>- if it doesn't return s up til that index |
| 27   | [Remove Element](https://leetcode.com/problems/remove-element/)                 | Easy       | Array          | - push all the non val elements to the back. keep track of a "last back" to keep the index of the last seen target val                                                                                |

---

_Back to [[Leetcode Tracking]]_
