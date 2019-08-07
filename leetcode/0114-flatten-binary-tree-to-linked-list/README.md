## Question

https://leetcode.com/problems/flatten-binary-tree-to-linked-list/

## Solutions

```go
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

	list := []*TreeNode{}
	preOrder(root, &list)

	for i := 1; i < len(list); i++ {
		root.Left = nil
		root.Right = list[i]
		root = root.Right
	}
}
```
