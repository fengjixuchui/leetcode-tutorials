## Question

https://leetcode.com/problems/coin-change-2/

## Solutions

```go
func change(amount int, coins []int) int {
	dp := make([]int, amount+1)
	dp[0] = 1

	for _, coin := range coins {
		for i := 1; i <= amount; i++ {
			if i-coin < 0 {
				continue
			}
			dp[i] += dp[i-coin]
		}
	}

	return dp[amount]
}
```
