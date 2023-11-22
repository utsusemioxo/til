# minimum path cost in a grid

[304. 网格中的最小路径代价](https://leetcode.cn/problems/minimum-path-cost-in-a-grid/description/)

## [记忆化搜索](#jump1)

记忆化搜索是一种动态规划的实现方式： 算法需要计算某个子问题的结果的时候，先检查是不是已经计算过该问题，如果计算过了，就直接返回已经存储的结果；否则计算该子问题的结果并将结果存储下来备用。

- 优点：代码清晰易懂，可以有效地处理复杂的状态转移方程。有些状态转移方程非常复杂，记忆搜索可以将复杂的状态转移方程拆分成多个子问题，通过递归调用解决。
- 缺点：可能会因为递归深度过大而导致栈溢出。

## [递推](#jump2)

递推也是一种动态规划的实现方式，递推`自底向上`地解决问题，采用循环的方式编写过程，先计算子问题，在过程中保存每一个子问题的解（通常保存在一个数组或者哈希表中）来避免重复计算。

- 优点：避免递归深度过大，调用栈溢出问题，计算顺序明确易于实现。
- 缺点：对于复杂的状态转移方程，代码实现会很困难。

## <span id="jump1">记忆化搜索代码</span>

```C++
class Solution {
public:
    int minPathCost(vector<vector<int>>& grid, vector<vector<int>>& moveCost) {
    
    }
};
```

## <span id="jump2">递推代码</span>

```C++
class Solution {
public:
    int minPathCost(vector<vector<int>>& grid, vector<vector<int>>& moveCost) {
      int n = grid.size();
      int m = grid.at(1).size();
      int res = INT_MAX;
      vector<vector<int>> ans(n, std::vector<int>(m, 0));
      for (int i = n-2; i >= 0; --i) {
        for(int j = m-1; j >= 0; --j) {
          int cost = 0;
          int min_res = INT_MAX;
          for(int k = 0; k <= m-1; ++k) {
            int temp_cost = 0;
            cost = moveCost.at(grid.at(i).at(j)).at(k);
            temp_cost = grid.at(i+1).at(k) + cost + grid.at(i).at(j);
            min_res = min(grid.at(i+1).at(k) + cost + grid.at(i).at(j), min_res);
          }
          grid.at(i).at(j) = min_res;
          if (i == 0 && grid.at(i).at(j) < res)
            res = grid.at(i).at(j);
        }
      }
      return res;
    }
};
```