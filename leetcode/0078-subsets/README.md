## Question

https://leetcode.com/problems/subsets/

## Solutions

```go
func backtrack(nums []int, start int, elem *[]int, results *[][]int) {
	*results = append(*results, append([]int{}, *elem...))

	for i := start; i < len(nums); i++ {
		*elem = append(*elem, nums[i])
		backtrack(nums, i+1, elem, results)
		*elem = (*elem)[:len(*elem)-1]
	}
}

func subsets(nums []int) [][]int {
	results := make([][]int, 0)
	elem := []int{}
	backtrack(nums, 0, &elem, &results)
	return results
}
```
