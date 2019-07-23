## Question

https://leetcode.com/problems/merge-two-binary-trees/

## Solutions

```go
func mergeTrees(t1 *TreeNode, t2 *TreeNode) *TreeNode {
	// Handle edge cases like:
	// t1: [], t2: [1]
	if t1 == nil {
		return t2
	}
	// t1: [1], t2: []
	if t2 == nil {
		return t1
	}

	t1.Val += t2.Val

	// If t1 left is empty then we append t2 left to t1.
	if t1.Left == nil && t2.Left != nil {
		t1.Left = t2.Left
	} else {
		// otherwise we just call the mergeTrees recursively.
		mergeTrees(t1.Left, t2.Left)
	}

	// If t1 right is empty then we append t2 right to t1.
	if t1.Right == nil && t2.Right != nil {
		t1.Right = t2.Right
	} else {
		// otherwise we just call the mergeTrees recursively.
		mergeTrees(t1.Right, t2.Right)
	}

	return t1
}
```
