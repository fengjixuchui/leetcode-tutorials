## Question

https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/

## Solutions

```go
func buildTreeHelper(post []int, postStart int, postEnd int, inStart int, inPos map[int]int) *TreeNode {
	if postStart > postEnd {
		return nil
	}

	root := &TreeNode{Val: post[postEnd]}
	rootIdx := inPos[post[postEnd]]
	leftLen := rootIdx - inStart
	root.Left = buildTreeHelper(post, postStart, postStart+leftLen-1, inStart, inPos)
	root.Right = buildTreeHelper(post, postStart+leftLen, postEnd-1, rootIdx+1, inPos)

	return root
}

func buildTree(inorder []int, postorder []int) *TreeNode {
	inPos := make(map[int]int)
	for i := 0; i < len(inorder); i++ {
		inPos[inorder[i]] = i
	}
	return buildTreeHelper(postorder, 0, len(postorder)-1, 0, inPos)
}
```
