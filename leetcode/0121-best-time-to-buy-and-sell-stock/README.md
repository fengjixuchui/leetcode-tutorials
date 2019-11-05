## Question

https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

## Solutions

```go
// O(n) time | O(1) space
func maxProfit(prices []int) int {
	if len(prices) == 0 {
		return 0
	}

	var maxProfit int
	buyPrice := prices[0]

	for i := 1; i < len(prices); i++ {
		potentialSellPrice := prices[i]
		if potentialSellPrice > buyPrice {
			profit := potentialSellPrice - buyPrice
			if profit > maxProfit {
				maxProfit = profit
			}
		} else {
			buyPrice = potentialSellPrice
		}
	}

	return maxProfit
}
```
