## Question

https://leetcode.com/problems/kth-largest-element-in-an-array

## Solutions

```go
func maxProfit(prices []int) int {
	if (len(prices) == 0) {
		return 0
	}

	max := 0
	buyPrice := prices[0]

	for _, price := range prices[1:] {
		if price < buyPrice {
			buyPrice = price
		} else {
			earn := price - buyPrice
			if earn > max {
				max = earn
			}
		}
	}

	return max
}
```
