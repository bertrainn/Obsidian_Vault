---
tags: [leetcode, two-pointers, algorithms]
created: 2025-06-27
updated: 2025-06-27
total_problems: 10
difficulty_breakdown:
  easy: 6
  medium: 4
  hard: 0
---

# ↔️ Two Pointers Problems

## 📊 Summary

- **Total Problems**: 10
- **Difficulty**: 6 Easy, 4 Medium

---

## Problems

| #    | Problem Name                                                                                                                                      | Difficulty | Algorithm Used | Optimal Solution                                                                                                                                                                                                                   |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 125  | [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)                                                                               | Easy       | 2 pointers     | - while l < r <br>- if either l or r isn't alnum iterate <br>- compare                                                                                                                                                             |
| 167  | [Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)                                             | Medium     | 2 Pointers     | - find the sum<br>- if sum too big decrement right<br>- if sum too small increase left                                                                                                                                             |
| 15   | [3Sum](https://leetcode.com/problems/3sum/)                                                                                                       | Medium     | 2 Pointers     | - sort the array<br>- 2 checks -> current num > 0, if the current num is the same as previous num<br>- do regular 2 sum with l r pointer<br>- when you hit, rmb to iterate the 2 pointers, (iterate L until you hit a diff number) |
| 11   | [Container With Most Water](https://leetcode.com/problems/container-with-most-water/)                                                             | Medium     | 2 Pointers     | - length = r - l <br>- basically check which height at l or r is bigger, and move the smaller height                                                                                                                               |
| 34   | [Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/) | Medium     | 2 Pointers     | - keep a left and right pointer, just keep decrementing and incrementing accordingly.                                                                                                                                              |
| 344  | [Reverse String](https://leetcode.com/problems/reverse-string/)                                                                                   | Easy       | 2 Pointers     | s[l], s[r] = s[r], s[l]                                                                                                                                                                                                            |
| 680  | [Valid Palindrome II](https://leetcode.com/problems/valid-palindrome-ii/)                                                                         | Easy       | 2 Pointers     | - define a "ispalindrome" function which does that<br>- run that function if you encounter a not matching function<br>                                                                                                             |
| 1768 | [Merge Strings Alternately](https://leetcode.com/problems/merge-strings-alternately/)                                                             | Easy       | 2 Pointers     | -use 2 pointers 1 for each string and iterate accordingly                                                                                                                                                                          |
| 88   | [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)                                                                           | Easy       | 2 Pointers     | - basically have 3 pointers<br>- fill num1 from the back<br>- edge case being, what if num1 had a bigger element than nums2 at the front. You would need to then fill the remaining elements from nums2 into nums1                 |
| 26   | [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)                                         | Easy       | 2 Pointer      | - start at index 1 and keep checking, <br>- if the values don't match, swap number at left with number at right<br>                                                                                                                |
| 658  | [Find K Closest Elements](https://leetcode.com/problems/find-k-closest-elements/)                                                                 | Medium     | 2 Pointers     | - one pointer at the end and start<br>- decrement R -> abs(arr[r] - x) >= abs(arr[l] - x) else increment L                                                                                                                         |

---

_Back to [[Leetcode Tracking]]_
