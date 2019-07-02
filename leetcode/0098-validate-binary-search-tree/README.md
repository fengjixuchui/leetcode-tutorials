## Question

https://leetcode.com/problems/validate-binary-search-tree/

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
func isValidBST(root *TreeNode) bool {
    return isValidBSTBound(root, nil, nil);
}

func isValidBSTBound(root *TreeNode, lower *TreeNode, upper *TreeNode) bool {
    if root == nil {
        return true
    }
    if lower != nil && lower.Val >= root.Val {
        return false
    }
    if upper != nil && upper.Val <= root.Val {
        return false
    }
    return isValidBSTBound(root.Left, lower, root) && isValidBSTBound(root.Right, root, upper);
}
```
