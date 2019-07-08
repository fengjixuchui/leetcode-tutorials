## Question

https://leetcode.com/problems/path-sum-iii/

## Solutions

```go
func pathSum(root *TreeNode, sum int) int {
    m := make(map[int]int, 0)
    m[0] = 1
    return dfs(root, 0, sum, m)
}

func dfs(root *TreeNode, curSum, sum int, m map[int]int) int{
    if root == nil {
        return 0
    }
    curSum += root.Val
    total := 0
    if val, ok := m[curSum - sum]; ok {
        total = val
    }
    m[curSum] = m[curSum] + 1
    total += dfs(root.Left, curSum, sum , m) + dfs(root.Right, curSum, sum , m)
    // key
    m[curSum] = m[curSum] -1

    return total
}
```
