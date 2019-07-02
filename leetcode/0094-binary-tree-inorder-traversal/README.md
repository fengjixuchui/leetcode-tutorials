## Question

https://leetcode.com/problems/binary-tree-inorder-traversal/

## Solutions

```go
func inorderTraversal(root *TreeNode) []int {
	stack := []*TreeNode{}
	result := []int{}

	for root != nil || len(stack) != 0 {
		for root != nil {
			stack = append(stack, root)
			root = root.Left
		}
		root = stack[len(stack)-1]
		stack = stack[:len(stack)-1]
		result = append(result, root.Val)
		root = root.Right
	}

	return result
}
```
