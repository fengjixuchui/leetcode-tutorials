## Question

https://leetcode.com/problems/binary-tree-maximum-path-sum/

## Solutions

```go
// O(n) time | O(1) space
func maxPathSum(root *TreeNode) int {
	max := math.MinInt32
	dfs(root, &max)
	return max
}

func dfs(root *TreeNode, max *int) int {
	if root == nil {
		return 0
	}

	left := Max(dfs(root.Left, max), 0)
	right := Max(dfs(root.Right, max), 0)
	cur := root.Val + left + right

	*max = Max(cur, *max)

	return root.Val + Max(left, right)
}

func Max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```

## Tutorials

- https://www.youtube.com/watch?v=uoRODgK0dIE
