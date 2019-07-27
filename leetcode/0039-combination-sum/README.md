## Question

https://leetcode.com/problems/combination-sum/

## Solutions

```go
func combSum(candidates []int, target int, start int, elem *[]int, results *[][]int) {
	if target < 0 {
		return
	}
	if target == 0 {
		*results = append(*results, append([]int{}, *elem...))
		return
	}
	for i := start; i < len(candidates); i++ {
		*elem = append(*elem, candidates[i])
		combSum(candidates, target-candidates[i], i, elem, results)
		*elem = (*elem)[:len(*elem)-1]
	}
}

func combinationSum(candidates []int, target int) [][]int {
	results := make([][]int, 0)
	elem := make([]int, 0)
	combSum(candidates, target, 0, &elem, &results)
	return results
}
```
