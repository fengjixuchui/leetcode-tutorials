## Question

https://leetcode.com/problems/0110-balanced-binary-tree/

## Solutions

```go
// Time: O(n), Space: O(1)
func isBalanced(root *TreeNode) bool {
	if root == nil {
		return true
	}
	if getHeightAndCheck(root) == -1 {
		return false
	}
	return true
}

func getHeightAndCheck(root *TreeNode) int {
	if root == nil {
		return 0
	}

	left := getHeightAndCheck(root.Left)
	right := getHeightAndCheck(root.Right)

	if left == -1 || right == -1 {
		return -1
	}

	if left-right > 1 || right-left > 1 {
		return -1
	}

	return max(left, right) + 1
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```

## Tutorials

- https://www.youtube.com/watch?v=nOcFiGl5Vy4
