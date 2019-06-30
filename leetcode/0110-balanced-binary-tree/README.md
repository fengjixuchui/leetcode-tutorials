## Question

https://leetcode.com/problems/0110-balanced-binary-tree/

## Solutions

```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func getHeightAndCheck(root *TreeNode) int {
	if root == nil {
		return 0
	}
	left := getHeightAndCheck(root.Left)
	if left == -1 {
		return -1
	}
	right := getHeightAndCheck(root.Right)
	if right == -1 {
		return -1
	}
	if int(math.Abs(float64(left-right))) > 1 {
		return -1
	}
	if left > right {
		return left + 1
	}
	return right + 1
}

func isBalanced(root *TreeNode) bool {
	return getHeightAndCheck(root) != -1
}
```
