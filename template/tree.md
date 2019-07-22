## Tree

```go
func preorderTraversal(root *TreeNode) []int {
	result := []int{}
	stack := []*TreeNode{}

	for root != nil || len(stack) != 0 {
		for root != nil {
            // Change this line below based on the questions.
            result = append(result, root.Val)
            // Change this line above based on the questions.
			stack = append(stack, root)
			root = root.Left
		}
		node := stack[len(stack)-1]
		stack = stack[0 : len(stack)-1]
		root = node.Right
	}

	return result
}
```
