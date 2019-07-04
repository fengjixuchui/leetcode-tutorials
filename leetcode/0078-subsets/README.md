## Question

https://leetcode.com/problems/subsets/

## Solutions

```go
func backtrack(nums []int, start int, elem []int, result *[][]int) {
	*result = append(*result, elem)

	for i := start; i < len(nums); i++ {
		temp := make([]int, len(elem))
		copy(temp, elem)
		backtrack(nums, i+1, append(temp, nums[i]), result)
	}
}

func subsets(nums []int) [][]int {
	result := make([][]int, 0)
	backtrack(nums, 0, []int{}, &result)
	return result
}
```
