## Question

https://leetcode.com/problems/binary-tree-level-order-traversal/

## Solutions

```go
// Time: O(n), Space: O(n)
func levelOrder(root *TreeNode) [][]int {
	if root == nil {
		return [][]int{}
	}

	queue := []*TreeNode{root}
	result := [][]int{}

	for len(queue) != 0 {
		currentLevel := []int{}
		size := len(queue)
		for i := 0; i < size; i++ {
			node := queue[0]
			queue = queue[1:]
			currentLevel = append(currentLevel, node.Val)
			if node.Left != nil {
				queue = append(queue, node.Left)
			}
			if node.Right != nil {
				queue = append(queue, node.Right)
			}
		}
		result = append(result, currentLevel)
	}

	return result
}
```
