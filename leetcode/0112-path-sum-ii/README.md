## Question

https://leetcode.com/problems/path-sum-ii/

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
func bt(root *TreeNode, sum int, elem *[]int, results *[][]int) {
	if root == nil {
		return
	}
	// if the slice change override the referecne slice.
	*elem = append(*elem, root.Val)
	if root.Left == nil && root.Right == nil && root.Val == sum {
		// prevent elements change in the next round.
		result := append([]int{}, *elem...)
		*results = append(*results, result)
	}
	bt(root.Left, sum-root.Val, elem, results)
	bt(root.Right, sum-root.Val, elem, results)
	*elem = (*elem)[:len(*elem)-1]
}

func pathSum(root *TreeNode, sum int) [][]int {
	results := make([][]int, 0)
	elem := make([]int, 0)
	bt(root, sum, &elem, &results)
	return results
}
```
