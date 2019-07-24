## Question

https://leetcode.com/problems/permutations/

## Solutions

```go
func bt(nums []int, results *[][]int, offset int) {
	if offset == len(nums) {
		*results = append(*results, append([]int{}, nums...))
		return
	}

	for i := offset; i < len(nums); i++ {
		swap(nums, offset, i)
		bt(nums, results, offset+1)
		swap(nums, offset, i)
	}
}

func permute(nums []int) [][]int {
	results := make([][]int, 0)
	bt(nums, &results, 0)
	return results
}

func swap(nums []int, a int, b int) {
	nums[a], nums[b] = nums[b], nums[a]
}
```
