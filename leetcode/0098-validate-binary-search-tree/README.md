## Question

https://leetcode.com/problems/validate-binary-search-tree/

## Solutions

```go
// Time: O(n) Space: O(log(n))
func isValidBST(root *TreeNode) bool {
	return isValid(root, nil, nil)
}

func isValid(root *TreeNode, lower *TreeNode, upper *TreeNode) bool {
	if root == nil {
		return true
	}
	if (lower != nil && root.Val <= lower.Val) || (upper != nil && root.Val >= upper.Val) {
		return false
	}
	return isValid(root.Left, lower, root) && isValid(root.Right, root, upper)
}
```
