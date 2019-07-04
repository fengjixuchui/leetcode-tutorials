## Question

https://leetcode.com/problems/jump-game/

## Solutions

```go
func canJump(nums []int) bool {
	if nums == nil || len(nums) == 0 {
		return false
	}

	n, max := len(nums), 0
	for i := 0; i < n; i++ {
		if i > max {
			return false
		}
		if max >= n-1 {
			return true
		}
		max = Max(max, i+nums[i])
	}

	return false
}

func Max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```
