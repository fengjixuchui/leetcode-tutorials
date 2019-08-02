## Question

https://leetcode.com/problems/0101-symmetric-tree/

## Solutions

```go
// Time: O(n) Space: O(log(n))
func isSymmetric(root *TreeNode) bool {
	if root == nil {
		return true
	}
	return isSame(root.Left, root.Right)
}

func isSame(left *TreeNode, right *TreeNode) bool {
	if left == nil && right == nil {
		return true
	}
	if (left != nil && right == nil) || (left == nil && right != nil) {
		return false
	}
	if left.Val != right.Val {
		return false
	}
	return isSame(left.Left, right.Right) && isSame(right.Left, left.Right)
}
```
