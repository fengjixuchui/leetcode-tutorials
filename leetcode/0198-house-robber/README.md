## Question

https://leetcode.com/problems/house-robber/

## Solutions

```go
func rob(nums []int) int {
	if len(nums) == 0 {
		return 0
	}
	if len(nums) == 1 {
		return nums[0]
	}

	d := make([]int, len(nums))
	d[0] = nums[0]
	d[1] = max(d[0], nums[1])

	for i := 2; i < len(nums); i++ {
		d[i] = max(d[i-1], d[i-2]+nums[i])
	}

	return d[len(nums)-1]
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```
