## Question

https://leetcode.com/problems/invert-binary-tree/

## Solutions

```go
// O(n) time | O(1) space
func invertTree(root *TreeNode) *TreeNode {
	if root == nil {
		return root
	}
	root.Left, root.Right = root.Right, root.Left
	invertTree(root.Left)
	invertTree(root.Right)
	return root
}
```
