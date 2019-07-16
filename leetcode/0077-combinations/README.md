## Question

https://leetcode.com/problems/combinations/

## Solutions

```go
func bt(n int, k int, start int, elem *[]int, results *[][]int) {
	if len(*elem) == k {
		result := append([]int{}, *elem...)
		*results = append(*results, result)
		return
	}

	for i := start; i <= n; i++ {
		*elem = append(*elem, i)
		bt(n, k, i+1, elem, results)
		*elem = (*elem)[:len(*elem)-1]
	}
}

func combine(n int, k int) [][]int {
	results := make([][]int, 0)
	elem := make([]int, 0)
	bt(n, k, 1, &elem, &results)
	return results
}
```
