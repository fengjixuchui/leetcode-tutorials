## Tree

### DFS

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

### BFS

```go
func levelOrderBottom(root *TreeNode) [][]int {
	if root == nil {
		return [][]int{}
	}

	queue := []*TreeNode{root}
	result := [][]int{}

	for len(queue) != 0 {
		currLevel := []int{}
		size := len(queue)
		for i := 0; i < size; i++ {
			node := queue[0]
			queue = queue[1:]
			currLevel = append(currLevel, node.Val)
			if node.Left != nil {
				queue = append(queue, node.Left)
			}
			if node.Right != nil {
				queue = append(queue, node.Right)
			}
		}
		// Change this line below based on the questions.
		result = append([][]int{currLevel}, result...)
		// Change this line below based on the questions.
	}

	return result
}
```
