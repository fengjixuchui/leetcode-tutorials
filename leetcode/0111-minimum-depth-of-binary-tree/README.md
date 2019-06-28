## Question

https://leetcode.com/problems/0111-minimum-depth-of-binary-tree/

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
func minDepth(root *TreeNode) int {
    if root == nil {
        return 0
    }
    if root.Left == nil && root.Right == nil {
        return 1
    }
    if root.Left == nil {
        return minDepth(root.Right) + 1
    }
    if root.Right == nil {
        return minDepth(root.Left) + 1
    }
    if (minDepth(root.Left) < minDepth(root.Right)) {
        return minDepth(root.Left) + 1
    } else {
        return minDepth(root.Right) + 1
    }
}
```
