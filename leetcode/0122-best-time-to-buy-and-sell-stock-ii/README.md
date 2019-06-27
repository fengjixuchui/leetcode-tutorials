## Question

https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/

## Solutions

```go
func maxProfit(prices []int) int {
	if len(prices) == 0 {
		return 0
	}

	profit := 0
	yesterdayPrice := prices[0]

	for _, todayPrice := range prices[1:] {
		if todayPrice > yesterdayPrice {
			earn := todayPrice - yesterdayPrice
			profit += earn
		}
		yesterdayPrice = todayPrice
	}

	return profit
}
```
