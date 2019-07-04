## Question

https://leetcode.com/problems/convert-bst-to-greater-tree/

## Solutions

```go
func convertBST(root *TreeNode) *TreeNode {
	stack := make([]*TreeNode, 0)
	sum := 0

	cur := root
	for cur != nil || len(stack) != 0 {
		for cur != nil {
			stack = append(stack, cur)
			cur = cur.Right
		}
		node := stack[len(stack)-1]
		stack = stack[0 : len(stack)-1]
		sum += node.Val
		node.Val = sum
		cur = node.Left
	}

	return root
}
```
