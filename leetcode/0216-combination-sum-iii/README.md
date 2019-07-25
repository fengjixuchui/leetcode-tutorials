## Question

https://leetcode.com/problems/combination-sum-iii/

```go
func bt(k int, sum int, start int, elem *[]int, results *[][]int) {
	if sum == 0 && len(*elem) == k {
		*results = append(*results, append([]int{}, *elem...))
	}

	for i := start; i <= 9; i++ {
		*elem = append(*elem, i)
		bt(k, sum-i, i+1, elem, results)
		*elem = (*elem)[:len(*elem)-1]
	}
}

func combinationSum3(k int, sum int) [][]int {
	results := [][]int{}
	elem := []int{}
	bt(k, sum, 1, &elem, &results)
	return results
}
```
