## Question

https://leetcode.com/problems/invert-binary-tree/

## Solutions

```go
// Time: O(n), Space: O(1)
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
