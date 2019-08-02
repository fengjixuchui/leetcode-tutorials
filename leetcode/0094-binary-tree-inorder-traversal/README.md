## Question

https://leetcode.com/problems/binary-tree-inorder-traversal/

## Solutions

```go
// Time: O(n), Space: O(n)
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

// Time: O(n), Space: O(n)
func inorderTraversal(root *TreeNode) []int {
	if root == nil {
		return []int{}
	}

	result := []int{}

	result = append(result, inorderTraversal(root.Left)...)
	result = append(result, root.Val)
	result = append(result, inorderTraversal(root.Right)...)

	return result
}
```
