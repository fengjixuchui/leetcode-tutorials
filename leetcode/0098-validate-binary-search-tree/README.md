## Question

https://leetcode.com/problems/validate-binary-search-tree/

## Solutions

```go
// O(n) time | O(1) space
func isValidBST(root *TreeNode) bool {
	return valid(root, nil, nil)
}

func valid(root, max, min *TreeNode) bool {
	if root == nil {
		return true
	}
  if (max != nil && root.Val >= max.Val) || (min != nil && root.Val <= min.Val) {
		return false
	}
	return valid(root.Left, root, min) && valid(root.Right, max, root)
}
```
