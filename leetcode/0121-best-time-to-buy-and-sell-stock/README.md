## Question

https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

## Solutions

```go
// Time: O(n), Space: O(1)
func maxProfit(prices []int) int {
	if prices == nil || len(prices) == 0 {
		return -1
	}

	maxProfit := 0
	lowest := prices[0]

	for i := 1; i < len(prices); i++ {
		if prices[i] > lowest {
			profit := prices[i] - lowest
			if profit > maxProfit {
				maxProfit = profit
			}
		} else {
			lowest = prices[i]
		}
	}

	return maxProfit
}
```
