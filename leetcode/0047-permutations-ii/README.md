## Question

https://leetcode.com/problems/permutations-ii/

## Solutions

```go
func dfs(nums []int, used map[int]bool, elem *[]int, results *[][]int) {
	if len(*elem) == len(nums) {
		result := []int{}
		*results = append(*results, append(result, *elem...))
		return
	}

	for i := 0; i < len(nums); i++ {
		if used[i] || (i > 0 && nums[i-1] == nums[i] && !used[i-1]) {
			continue
		}
		used[i] = true
		*elem = append(*elem, nums[i])
		dfs(nums, used, elem, results)
		used[i] = false
		*elem = (*elem)[:len(*elem)-1]
	}
}

func permuteUnique(nums []int) [][]int {
	sort.Ints(nums)
	results := make([][]int, 0)
	elem := make([]int, 0)
	used := make(map[int]bool, 0)
	dfs(nums, used, &elem, &results)
	return results
}
```
