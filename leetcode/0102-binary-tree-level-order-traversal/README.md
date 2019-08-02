## Question

https://leetcode.com/problems/binary-tree-level-order-traversal/

## Solutions

```go
// Time: O(n), Space: O(n)
func levelOrder(root *TreeNode) [][]int {
	if root == nil {
		return [][]int{}
	}

	stack := []*TreeNode{root}
	result := [][]int{}

	for len(stack) != 0 {
		curLevel := []int{}
		nextLevel := []*TreeNode{}
		for len(stack) != 0 {
			node := stack[0]
			stack = stack[1:]
			curLevel = append(curLevel, node.Val)
			if node.Left != nil {
				nextLevel = append(nextLevel, node.Left)
			}
			if node.Right != nil {
				nextLevel = append(nextLevel, node.Right)
			}

		}
		result = append(result, curLevel)
		stack = nextLevel
	}

	return result
}
```
