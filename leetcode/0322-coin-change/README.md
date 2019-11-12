## Question

https://leetcode.com/problems/coin-change/

## Solutions

```go
// O(n^2) time | O(n) space
func coinChange(coins []int, amount int) int {
	dp := make([]int, amount+1)
	for i := 0; i <= amount; i++ {
		dp[i] = amount + 1
	}

	dp[0] = 0

	for i := 0; i <= amount; i++ {
		for j := 0; j < len(coins); j++ {
			if i >= coins[j] {
				dp[i] = min(dp[i], 1+dp[i-coins[j]])
			}
		}
	}

	if dp[amount] > amount {
		return -1
	}
	return dp[amount]
}

func min(a, b int) int {
	if a > b {
		return b
	}
	return a
}
```

## Tutorials

- https://www.youtube.com/watch?v=1R0_7HqNaW0
