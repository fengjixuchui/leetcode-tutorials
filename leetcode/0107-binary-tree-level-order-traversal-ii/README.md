## Question

https://leetcode.com/problems/0107-binary-tree-level-order-traversal-ii/

## Solutions

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
		result = append([][]int{currLevel}, result...)
	}

	return result
}
```
