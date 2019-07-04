## Question

https://leetcode.com/problems/combination-sum/

## Solutions

```go
func combSum(candidates []int, target int, start int, elem []int, result *[][]int) {
	if target == 0 {
		*result = append(*result, elem)
		return
	}
	if target < 0 {
		return
	}
	for i := start; i < len(candidates); i++ {
		tmp := make([]int, len(elem))
		copy(tmp, elem)
		combSum(candidates, target-candidates[i], i, append(tmp, candidates[i]), result)
	}
}

func combinationSum(candidates []int, target int) [][]int {
	result := make([][]int, 0)
	combSum(candidates, target, 0, []int{}, &result)
	return result
}
```
