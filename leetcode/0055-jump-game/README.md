## Question

https://leetcode.com/problems/jump-game/

## Solutions

```go
// O(n) time | O(1) space
func canJump(nums []int) bool {
	if nums == nil || len(nums) == 0 {
		return false
	}

	maxIdx := 0
	for i := 0; i < len(nums); i++ {
		if i > maxIdx {
			return false
		}
		maxIdx = max(maxIdx, i+nums[i])
	}

	return true
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```
