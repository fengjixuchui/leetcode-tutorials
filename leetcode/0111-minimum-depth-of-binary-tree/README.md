## Question

https://leetcode.com/problems/0111-minimum-depth-of-binary-tree/

## Solutions

```go
func minDepth(root *TreeNode) int {
	if root == nil {
		return 0
    }

	left := minDepth(root.Left)
    right := minDepth(root.Right)

	if left == 0 {
		return right + 1
	} else if right == 0 {
		return left + 1
	}
	return Min(left, right) + 1
}

func Min(a, b int) int {
	if a > b {
		return b
	}
	return a
}
```
