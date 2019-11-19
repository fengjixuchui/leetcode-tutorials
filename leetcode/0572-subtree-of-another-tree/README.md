## Question

https://leetcode.com/problems/subtree-of-another-tree/

## Solutions

```go
// Time: O(n), Space: O(1)
func isSubtree(s *TreeNode, t *TreeNode) bool {
	if s == nil {
		return false
	}
	if isSameTree(s, t) {
		return true
	}
	return isSubtree(s.Left, t) || isSubtree(s.Right, t)
}

func isSameTree(s *TreeNode, t *TreeNode) bool {
	if s == nil && t == nil {
		return true
	}
	if s == nil || t == nil {
		return false
	}
	return s.Val == t.Val && isSameTree(s.Left, t.Left) && isSameTree(s.Right, t.Right)
}
```

## Tutorials

- https://www.youtube.com/watch?v=nVjxiBieE1w
