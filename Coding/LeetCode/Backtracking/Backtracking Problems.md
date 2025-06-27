---
tags: [leetcode, backtracking, algorithms]
created: 2025-06-27
updated: 2025-06-27
total_problems: 6
difficulty_breakdown:
  easy: 0
  medium: 6
  hard: 0
---

# 🔄 Backtracking Problems

## 📊 Summary

- **Total Problems**: 6
- **Difficulty**: 6 Medium

---

## Problems

| #   | Problem Name                                                                                                  | Difficulty | Algorithm Used | Optimal Solution                                                                                                                                                                                                                                                                                                                                                                                                                            |
| --- | ------------------------------------------------------------------------------------------------------------- | ---------- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 78  | [Subsets](https://leetcode.com/problems/subsets/)                                                             | Medium     | Backtracking   | - res and solution global variables<br>- define base case (index == len of nums), add copy of solution to res<br>- option A -> don't add value, conduct backtracking<br>- option B -> add value, backtrack, remove said value                                                                                                                                                                                                               |
| 46  | [Permutations](https://leetcode.com/problems/permutations/)                                                   | Medium     | Backtracking   | - res and sol global variables<br>- basecase -> len(sol) == len(nums): append sol to res<br>- go down the path of using a number if it is not in the sol                                                                                                                                                                                                                                                                                    |
| 77  | [Combinations](https://leetcode.com/problems/combinations/)                                                   | Medium     | Backtracking   | - res and sol global variables<br>- basecase -> len(sol) == k: append a copy of sol to res<br>- build the combinations from the nth value downwards<br>- way to make is faster is to check if the number of values left > the number of values needed                                                                                                                                                                                       |
| 39  | [Combination Sum](https://leetcode.com/problems/combination-sum/)                                             | Medium     | Backtracking   | backtrack(index, cursum)<br>- basecase: current sum == target -> save the solutions<br>- terminate early case: cursum > target or i == len(list)<br>- option 1: don't choose current index: backtrack(index + 1, cursum)<br>- option 2: choose current index: <br>sol.append(value)<br>backtrack(i, cursum + value)<br>sol.pop()<br>it's always add, backtrack, remove                                                                      |
| 17  | [Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/) | Medium     | Backtracking   | backtracking keep a index<br>- basecase: index == len(digits string)<br>- just a simple forloop that iterates through a map of possible letters <br>- same as usual -> add, backtrack, pop                                                                                                                                                                                                                                                  |
| 22  | [Generate Parentheses](https://leetcode.com/problems/generate-parentheses/)                                   | Medium     | Backtracking   | backtrack(open, close)<br>open -> no. of (, close -> no. of )<br>- basecase: len(sol) == 2 \* n<br>- if open < n -> add (, backtrack, pop<br>- if close < open -> add ), backtrack, pop<br><br>open can never be more than n<br>close can never be more than open                                                                                                                                                                           |
| 79  | [Word Search](https://leetcode.com/problems/word-search/)                                                     | Medium     | Backtracking   | backtrack (pos, index of text)<br>- basecase: index == len of word<br>- early termination: current text != letter at index<br>- save the current char we are looking at, mark the position out with a non-character (#)<br>- do backtrack on surrounding board char (up down left right) -> return true if backtrack success, else fail<br>-- Check if we in bounds (if 0 <= x/ y < COL/ ROW)<br>-restore the character at position<br><br> |

---

## Notes

### Backtracking Template

```python
def backtracking():
	if (some base case):
		some random modification
		return

	backtracking(a) -> take option A

	some modification -> take option B
	backtracking(b) -> continue with option B
	undo option B
```

### Key Principles

1. **Make** a choice
2. **Recurse** with that choice
3. **Undo** the choice (restore state)

---

_Back to [[Leetcode Tracking]]_
