## Question

https://leetcode.com/problems/print-binary-tree/

## Solutions

```go
func getHight(root *TreeNode) int {
	if root == nil {
		return 0
	}
	return Max(getHight(root.Left), getHight(root.Right)) + 1
}

func fill(root *TreeNode, ans *[][]string, h, l, r int) {
	if root == nil {
		return
	}
	mid := l + (r-l)/2
	(*ans)[h][mid] = strconv.Itoa(root.Val)
	fill(root.Left, ans, h+1, l, mid-1)
	fill(root.Right, ans, h+1, mid+1, r)
}

func printTree(root *TreeNode) [][]string {
	h := getHight(root)
	w := (1 << uint(h)) - 1 // 2 ^ h - 1
	ans := make([][]string, h)
	for i := 0; i < len(ans); i++ {
		ans[i] = make([]string, w)
	}
	fill(root, &ans, 0, 0, w-1)
	return ans
}

func Max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```
