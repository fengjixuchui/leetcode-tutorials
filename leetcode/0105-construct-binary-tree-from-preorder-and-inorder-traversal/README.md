## Question

https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/

## Solutions

```go
// Time: O(n) Space: O(n)
func buildTreeHelper(pre []int, preStart int, preEnd int, inStart int, inPos map[int]int) *TreeNode {
	if preStart > preEnd {
		return nil
	}

	root := &TreeNode{Val: pre[preStart]}
	rootIdx := inPos[pre[preStart]]
	leftLen := rootIdx - inStart
	root.Left = buildTreeHelper(pre, preStart+1, preStart+leftLen, inStart, inPos)
	root.Right = buildTreeHelper(pre, preStart+leftLen+1, preEnd, rootIdx+1, inPos)

	return root
}

func buildTree(preorder []int, inorder []int) *TreeNode {
	inPos := make(map[int]int)
	for i := 0; i < len(inorder); i++ {
		inPos[inorder[i]] = i
	}
	return buildTreeHelper(preorder, 0, len(preorder)-1, 0, inPos)
}
```

## Tutorals

- https://www.youtube.com/watch?v=PoBGyrIWisE
