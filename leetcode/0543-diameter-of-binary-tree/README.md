## Question

https://leetcode.com/problems/diameter-of-binary-tree/

## Solutions

```go
func maxDepth(root *TreeNode, d []int) int {
	if root == nil {
		return 0
	}
	left := maxDepth(root.Left, d)
	right := maxDepth(root.Right, d)
	d[0] = max(d[0], left+right)
	return max(left, right) + 1
}

func diameterOfBinaryTree(root *TreeNode) int {
	d := make([]int, 1)
	maxDepth(root, d)
	return d[0]
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```
