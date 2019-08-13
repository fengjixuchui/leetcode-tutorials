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

	maxProfit := make([]int, len(nums))
	maxProfit[0], maxProfit[1] = nums[0], Max(nums[0], nums[1])

	for i := 2; i < len(nums); i++ {
		// maxProfit[i-1]         -> didn't rob the current house
		// nums[i]+maxProfit[i-2] -> rob the current house
		maxProfit[i] = Max(maxProfit[i-1], nums[i]+maxProfit[i-2])
	}

	return maxProfit[len(maxProfit)-1]
}

func Max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```
