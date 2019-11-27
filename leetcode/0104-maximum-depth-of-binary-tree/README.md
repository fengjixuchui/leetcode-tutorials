## Question

https://leetcode.com/problems/maximum-depth-of-binary-tree/

## Solutions

```go
// Time: O(n), Space: O(1)
func maxDepth(root *TreeNode) int {
	if root == nil {
		return 0
	}

  	left := maxDepth(root.Left)
	right := maxDepth(root.Right)

	if left > right {
		return 1 + left
	}
	return 1 + right
}
```
