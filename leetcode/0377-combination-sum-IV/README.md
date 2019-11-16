## Question

https://leetcode.com/problems/combination-sum-iv

## Solutions

```go
// Time: O(m*n), Space: O(m)
func combinationSum4(nums []int, target int) int {
	dp := make([]int, target+1)
	dp[0] = 1
	for i := 1; i < target; i++ {
		for j := 0; j < len(nums); j++ {
			if nums[j] > i {
				continue
			}
			dp[i] += dp[i-nums[j]]
		}
	}
	return dp[target]
}
```

## Tutorials

- https://www.youtube.com/watch?v=yNq7JFd7sHE
