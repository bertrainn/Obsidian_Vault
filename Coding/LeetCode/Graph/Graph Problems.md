---
tags: [leetcode, graph, dfs, bfs, algorithms]
created: 2025-06-27
updated: 2025-06-27
total_problems: 6
difficulty_breakdown:
  easy: 1
  medium: 5
  hard: 0
---

# 🕸️ Graph Problems

## 📊 Summary

- **Total Problems**: 6
- **Difficulty**: 1 Easy, 5 Medium

---

## Problems

| #    | Problem Name                                                                                | Difficulty | Algorithm Used | Optimal Solution                                                                                                                                                                                                                                                                                                                                                                                                        |
| ---- | ------------------------------------------------------------------------------------------- | ---------- | -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1971 | [Find if Path Exists in Graph](https://leetcode.com/problems/find-if-path-exists-in-graph/) | Easy       | Graph          | - DFS on the graph<br>- for each neighbour from the node graph, append the neighbour into the seen set<br>- run DFS on the neighbour (i.e. let that shit run)                                                                                                                                                                                                                                                           |
| 200  | [Number of Islands](https://leetcode.com/problems/number-of-islands/)                       | Medium     | Graph          | - Run a DFS on the grid <br>- basically the DFS is to set the island to 0 not to count the island, cause we are checking if the value is 1 to run the DFS                                                                                                                                                                                                                                                               |
| 695  | [Max Area of Island](https://leetcode.com/problems/max-area-of-island/)                     | Medium     | Graph          | - Similar idea to the previous qns, actually it's straight up the same<br>- just keep track of the size of the island by returning 1 + dfs of left right up down                                                                                                                                                                                                                                                        |
| 207  | [Course Schedule](https://leetcode.com/problems/course-schedule/)                           | Medium     | Graph          | - Similar to [Find if Path Exists in Graph](https://leetcode.com/problems/find-if-path-exists-in-graph/) -> DFS logic wise<br>- keep a state array of 3 states (unseen, seeing, seen)<br>- idea is to find a cycle in the graph -> cycle being if a seeing node finds another seeing node<br>- when you first enter a node -> set it to SEEING<br>- do DFS<br>- After DFS change that node state to seen -> return true |
| 210  | [Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)                     | Medium     | Graph          | IT'S THE SAME FUKIN CODE WTS                                                                                                                                                                                                                                                                                                                                                                                            |
| 417  | [Pacific Atlantic Water Flow](https://leetcode.com/problems/pacific-atlantic-water-flow/)   | Medium     | Graph          | - The idea is to see if the water can get from the edge to said square. (everything on the edge can go into the ocean)<br>- Put all edge elements into a set and queue<br>- Run a bfs/ dfs (doesn't rly matter)<br>- intersection of the results                                                                                                                                                                        |

---

## Notes

### Graph Fundamentals

- Use a seen set to keep track of seen nodes
- **DFS** -> uses stack (iterative) or recursive stack
- **BFS** -> Queue

### Building Adjacency List

```python
graph = defaultdict(list)
for u, v in edges:
	graph[u].append(v)
	graph[v].append(u)

example:
edges = [[0,1],[1,2],[2,0]]
graph = {0: [1, 2], 1: [0, 2], 2: [1, 0]}
```

---

_Back to [[Leetcode Tracking]]_
