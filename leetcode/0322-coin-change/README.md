## Question

https://leetcode.com/problems/coin-change/

## Solutions

```go
func coinChange(coins []int, amount int) int {
	dp := make([]int, amount+1)
	for i := 0; i <= amount; i++ {
		dp[i] = math.MaxInt32
	}
	dp[0] = 0

	for i := 1; i <= amount; i++ {
		for j := 0; j < len(coins); j++ {
			if i-coins[j] < 0 {
				continue
			}
			dp[i] = min(dp[i], 1+dp[i-coins[j]])
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
