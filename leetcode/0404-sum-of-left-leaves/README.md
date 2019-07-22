## Question

https://leetcode.com/problems/sum-of-left-leaves/

## Solutions

```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func sumOfLeftLeaves(root *TreeNode) int {
	sum := 0
	stack := []*TreeNode{}

	for root != nil || len(stack) != 0 {
		for root != nil {
			if root.Left != nil && root.Left.Left == nil && root.Left.Right == nil {
				sum += root.Left.Val
			}
			stack = append(stack, root)
			root = root.Left
		}
		node := stack[len(stack)-1]
		stack = stack[0 : len(stack)-1]
		root = node.Right
	}

	return sum
}
```
