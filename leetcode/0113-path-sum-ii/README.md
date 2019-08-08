## Question

https://leetcode.com/problems/path-sum-ii/

## Solutions

```go
func dfs(root *TreeNode, sum int, elem *[]int, results *[][]int) {
	if root == nil {
		return
	}
	// if the slice change override the referecne slice.
	*elem = append(*elem, root.Val)
	if root.Left == nil && root.Right == nil && root.Val == sum {
		// prevent elements change in the next round.
		*results = append(*results, append([]int{}, *elem...))
	}
	dfs(root.Left, sum-root.Val, elem, results)
	dfs(root.Right, sum-root.Val, elem, results)
	*elem = (*elem)[:len(*elem)-1]
}

func pathSum(root *TreeNode, sum int) [][]int {
	results := make([][]int, 0)
	elem := make([]int, 0)
	dfs(root, sum, &elem, &results)
	return results
}
```
