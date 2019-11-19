## Question

https://leetcode.com/problems/validate-binary-search-tree/

## Solutions

```go
// Time: O(n), Space: O(1)
func isValidBST(root *TreeNode) bool {
	if root == nil {
		return true
	}
	return isValid(root, nil, nil)
}

func isValid(root, upperBound, lowerBound *TreeNode) bool {
	if root == nil {
		return true
	}

	if (upperBound != nil && root.Val >= upperBound.Val) || (lowerBound != nil && root.Val <= lowerBound.Val) {
		return false
	}

	return isValid(root.Left, root, lowerBound) && isValid(root.Right, upperBound, root)
}
```

## Tutorials

- https://www.youtube.com/watch?v=ofuXorE-JKE
