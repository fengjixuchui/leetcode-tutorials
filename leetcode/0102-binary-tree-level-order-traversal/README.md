## Question

https://leetcode.com/problems/binary-tree-level-order-traversal/

## Solutions

```go
// Time: O(n), Space: O(n)
func levelOrder(root *TreeNode) [][]int {
	res := [][]int{}

	if root == nil {
		return res
	}

	q := []*TreeNode{root}

	for len(q) != 0 {
		length := len(q)
		level := []int{}
		for i := 0; i < length; i++ {
			node := q[0]
			q = q[1:]
			level = append(level, node.Val)
			if node.Left != nil {
				q = append(q, node.Left)
			}
			if node.Right != nil {
				q = append(q, node.Right)
			}
		}
		res = append(res, level)
	}

	return res
}
```
