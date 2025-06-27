---
tags: [leetcode, binary-search, algorithms]
created: 2025-06-27
updated: 2025-06-27
total_problems: 3
difficulty_breakdown:
  easy: 0
  medium: 3
  hard: 0
---

# 🔍 Binary Search Problems

## 📊 Summary

- **Total Problems**: 3
- **Difficulty**: 3 Medium

---

## Problems

| #   | Problem Name                                                                                                | Difficulty | Algorithm Used | Optimal Solution                                                                                                                                                                                                                                          |
| --- | ----------------------------------------------------------------------------------------------------------- | ---------- | -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 153 | [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/) | Medium     | Binary Search  | Binary Search <br>check if the nums[middle] > nums[right], if it is close off l to middle + 1 else r = m<br>                                                                                                                                              |
| 33  | [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)             | Medium     | Binary Search  | - Do a find min in rotated sorted array first to create a partition<br>- Find L, R pointers based on which partition the target is in<br>- Do regular BS within the partition                                                                             |
| 875 | [Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/)                                   | Medium     | Binary Search  | - L, R = 1 and max(amount possible), rate = (l + r) // 2<br>- Calc the total hours it takes to eat the piles at that rate.<br>- if total_time_taken <= h -> we too fast can go slower<br>- else total_time_taken > h -> we too slow go faster<br>return r |

---

## Notes

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

_Back to [[Leetcode Tracking]]_
