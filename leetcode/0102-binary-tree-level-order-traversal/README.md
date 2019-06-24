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
func levelOrder(root *TreeNode) [][]int {
	res := make([][]int, 0)

	if root == nil {
		return res
	}

	q := make([]*TreeNode, 0)
	q = append(q, root)

	for len(q) > 0 {
		curLayerCount := len(q)
		curLayer := make([]int, 0)
		for i := 0; i < curLayerCount; i++ {
			n := q[0]
			q = q[1:]
			curLayer = append(curLayer, n.Val)
			if n.Left != nil {
				q = append(q, n.Left)
			}
			if n.Right != nil {
				q = append(q, n.Right)
			}
		}
		res = append(res, curLayer)
	}

	return res
}
```
