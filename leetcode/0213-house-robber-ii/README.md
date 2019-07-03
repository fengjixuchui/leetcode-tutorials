## Question

https://leetcode.com/problems/house-robber-ii/

## Solutions

```go
func helper(nums []int) int {
	if len(nums) == 1 {
		return nums[0]
	}

	records := make(map[int]int, len(nums))
	records[0] = nums[0]
	records[1] = Max(nums[0], nums[1])

	for i := 2; i < len(nums); i++ {
		records[i] = Max(nums[i]+records[i-2], records[i-1])
	}

	return records[len(nums)-1]
}

func Max(a, b int) int {
	if a > b {
		return a
	}
	return b
}

func rob(nums []int) int {
	if nums == nil || len(nums) == 0 {
		return 0
	}
	if len(nums) == 1 {
		return nums[0]
	}
	return Max(helper(nums[1:]), helper(nums[:len(nums)-1]))
}
```
