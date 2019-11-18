## Question

https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/

## Solutions

```go
// O(n) time | O(1) space
func lowestCommonAncestor(root, p, q *TreeNode) *TreeNode {
	if root == nil {
		return nil
	}

	if root == q || root == p {
		return root
	}

	left := lowestCommonAncestor(root.Left, p, q)
	right := lowestCommonAncestor(root.Right, p, q)

	if left != nil && right == nil {
		return left
	} else if left == nil && right != nil {
		return right
	} else if left != nil && right != nil {
		return root
	} else {
		// left == nil && right == nil
		return nil
	}
}
```

## Tutorials

- https://www.youtube.com/watch?v=13m9ZCB8gjw
