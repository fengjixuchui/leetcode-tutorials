## Question

https://leetcode.com/problems/permutations/

## Solutions

```go
func bt(nums []int, ans *[][]int, offset int) {
	if offset == len(nums) {
		t := make([]int, len(nums))
		copy(t, nums)
		*ans = append(*ans, t)
		return
	}

	for i := offset; i < len(nums); i++ {
		swap(nums, offset, i)
		bt(nums, ans, offset+1)
		swap(nums, offset, i)
	}
}

func permute(nums []int) [][]int {
	ans := make([][]int, 0)
	bt(nums, &ans, 0)
	return ans
}

func swap(nums []int, a int, b int) {
	nums[a], nums[b] = nums[b], nums[a]
}
```
