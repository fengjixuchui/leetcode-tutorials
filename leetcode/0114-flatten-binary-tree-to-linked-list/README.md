## Question

https://leetcode.com/problems/flatten-binary-tree-to-linked-list/

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
func preOrder(root *TreeNode, list *[]*TreeNode) {
	if root == nil {
		return
	}
	*list = append(*list, root)
	preOrder(root.Left, list)
	preOrder(root.Right, list)
}

func flatten(root *TreeNode) {
	if root == nil {
		return
	}

	list := make([]*TreeNode, 0)
	preOrder(root, &list)

	cur := root
	for i := 1; i < len(list); i++ {
		cur.Left = nil
		cur.Right = list[i]
		cur = cur.Right
	}
}
```
