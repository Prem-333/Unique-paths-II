# Unique Paths II - LeetCode Solution (Python)

## 📌 Problem Description
A robot is located at the top-left corner of an `m x n` grid. The robot can only move either down or right at any point in time. The grid contains obstacles marked as `1`, and free spaces as `0`. The robot cannot move onto obstacles.

**Goal:** Find the number of unique paths from the top-left corner to the bottom-right corner of the grid.

### Example:
Input:
obstacleGrid = [[0,0,0],[0,1,0],[0,0,0]]

Output:
2

yaml
Copy
Edit
Explanation: There are two unique paths:
- Right → Right → Down → Down
- Down → Down → Right → Right

---

## ✅ Constraints
- `1 <= m, n <= 100`
- `obstacleGrid[i][j]` is `0` (empty) or `1` (obstacle)
- The start and end cell will not be an obstacle

---

## ✅ Approach (Dynamic Programming)
- Use **Dynamic Programming** to compute the number of ways.
- If `obstacleGrid[i][j] == 1` → set `dp[j] = 0` (cannot pass through obstacle)
- Otherwise, `dp[j] += dp[j - 1]` (ways from top + left)
- Space optimized to **O(n)** using a single row DP array.

---

## ✅ Optimized Python Code (O(m*n) time | O(n) space)
```python
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid):
        m, n = len(obstacleGrid), len(obstacleGrid[0])
        dp = [0] * n
        dp[0] = 1 if obstacleGrid[0][0] == 0 else 0

        for i in range(m):
            for j in range(n):
                if obstacleGrid[i][j] == 1:
                    dp[j] = 0
                elif j > 0:
                    dp[j] += dp[j - 1]
        return dp[-1]
✅ Complexity Analysis
Time Complexity: O(m * n) (iterate through all cells)

Space Complexity: O(n) (1D DP array)

✅ Alternative Approaches
Full DP Table (O(m*n) space): Use a 2D DP array

In-place DP: Modify the obstacleGrid directly to save space

🔗 Related Problems
Unique Paths I (LeetCode 62)

yaml
Copy
Edit

---

📌 Do you want me to **also include:**
✅ Example **Input/Output screenshots**,  
✅ **Dry run diagram**,  
✅ Or make this into a **GitHub-ready repository with README + Code + Test cases**?  
