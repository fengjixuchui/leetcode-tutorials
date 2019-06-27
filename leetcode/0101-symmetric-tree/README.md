## Question

https://leetcode.com/problems/0101-symmetric-tree/

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
func helper(left *TreeNode, right *TreeNode) bool {
	if left != nil && right != nil {
		if left.Val != right.Val {
			return false
		}
		return helper(left.Left, right.Right) && helper(left.Right, right.Left)
	}
	return left == nil && right == nil
}

func isSymmetric(root *TreeNode) bool {
	if root == nil {
		return true
	}
	return helper(root.Left, root.Right)
}
```
