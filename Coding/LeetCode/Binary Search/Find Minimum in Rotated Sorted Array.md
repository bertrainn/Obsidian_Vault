---
title: "[LeetCode] 153. Find Minimum in Rotated Sorted Array"
tags:
  - leetcode
  - Binary_Search
difficulty: Medium
status: Solved
date: 2025-06-11
link: https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/
time_taken: <e.g., 30min>
language: <e.g., Python3>
---

## 🧠 Problem Summary

> In an array of length N, sorted in ascending order rotated from 1 to N times. Find the Min Value

## 🔍 Constraints & Edge Cases

- 
- 
- 

## 🛠️ Approach

**1st Attempt**  
Explain your first thought process and strategy.

**Optimized Solution**  
Describe improvements, trade-offs, or alternate approaches.

## 🧪 Test Cases

| Input | Expected Output | Notes |
|-------|------------------|-------|
|       |                  |       |
|       |                  |       |

## 💻 Code

### ✅ Final Solution (Python)

```python

def findMin(self, nums: List[int]) -> int:
	l, r = 0, len(nums) - 1
	while l < r:
		m = (l + r) // 2
		if nums[m] > nums[r]:
			l = m + 1
		else:
			r = m
	return nums[l]
```

