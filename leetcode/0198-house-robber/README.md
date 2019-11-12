## Question

https://leetcode.com/problems/house-robber/

## Solutions

```go
// Time: O(n), Space: O(n)
func rob(nums []int) int {
	if nums == nil || len(nums) == 0 {
		return 0
	}
	if len(nums) == 1 {
		return nums[0]
	}

	records := make([]int, len(nums))
	records[0] = nums[0]
	records[1] = max(nums[0], nums[1])

	for i := 2; i < len(nums); i++ {
		records[i] = max(nums[i]+records[i-2], records[i-1])
	}

	return records[len(nums)-1]
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```
