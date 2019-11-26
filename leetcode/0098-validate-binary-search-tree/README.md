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

func isValid(cur, max, min *TreeNode) bool {
	if cur == nil {
		return true
	}

	if max != nil && cur.Val >= max.Val {
		return false
	}

	if min != nil && cur.Val <= min.Val {
		return false
	}

	return isValid(cur.Left, cur, min) && isValid(cur.Right, max, cur)
}
```

## Tutorials

- https://www.youtube.com/watch?v=ofuXorE-JKE
