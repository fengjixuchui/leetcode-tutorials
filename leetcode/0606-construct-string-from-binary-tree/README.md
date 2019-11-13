## Question

https://leetcode.com/problems/construct-string-from-binary-tree/

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
func tree2str(t *TreeNode) string {
	if t == nil {
		return ""
	}

	s := strconv.Itoa(t.Val)
	l := tree2str(t.Left)
	r := tree2str(t.Right)

	// case 0: s
	if t.Left == nil && t.Right == nil {
		return s
	} else if t.Right == nil {
		// case 0: s(l)
		return s + "(" + l + ")"
	} else {
		// case 0: s(l)(r)
		return s + "(" + l + ")" + "(" + r + ")"
	}
}
```

