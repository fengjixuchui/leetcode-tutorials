## Question

https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

## Solutions

```go
func maxProfit(prices []int) int {
	profits := make([]int, len(prices))
	max := 0

	lowest := math.MaxInt32
	for i := 0; i < len(prices); i++ {
		lowest = Min(lowest, prices[i])
		profits[i] = prices[i] - lowest
		if profits[i] > max {
			max = profits[i]
		}
	}

	return max
}

func Min(a, b int) int {
	if b > a {
		return a
	}
	return b
}
```
