## Backtracking

通用模板

```go
func bt(root *TreeNode, sum int, elem *[]int, results *[][]int) {
	// 終止條件
	if {
		// 這裡必須拷貝一份答案
		// 因為後面會繼續遞歸，不拷貝的話最后答案會全部變成一個錯的值
		result := append([]int{}, *elem...)
		*results = append(*results, result)
	}

	// 添加元素
	*elem = append(*elem, root.Val)

	// 遞歸
	bt(root.Left, sum-root.Val, elem, results)
	bt(root.Right, sum-root.Val, elem, results)

	// 回退
	*elem = (*elem)[:len(*elem)-1]
}

func pathSum(root *TreeNode, sum int) [][]int {
	results := make([][]int, 0)
	elem := make([]int, 0)
	// 記住要傳 pointer 下去，避免 slice 擴容改掉當前參照的 slice
	bt(root, sum, &elem, &results)
	return results
}
```
