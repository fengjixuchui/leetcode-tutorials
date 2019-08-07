## Question

https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/

## Solutions

```go
// Time: O(nk), Space: O(nk)
func maxProfit(k int, prices []int) int {
	if len(prices) == 0 {
		return 0
	}

	// degrade to: best-time-to-buy-and-sell-stock-ii
	if k > len(prices)/2 {
		profit := 0
		for i := 1; i < len(prices); i++ {
			profit += Max(0,prices[i]-prices[i-1])
		}
		return profit
	}

	// row   : transactions
	// column: days
	profits := make([][]int, k+1)
	for t := 0; t < len(profits); t++ {
		profits[t] = make([]int, len(prices))
	}

	for t := 1; t < k+1; t++ {
		maxThusFar := math.MinInt32
		for d := 1; d < len(prices); d++ {
			maxThusFar = Max(maxThusFar, profits[t-1][d-1]-prices[d-1])
			profits[t][d] = Max(profits[t][d-1], maxThusFar+prices[d])
		}
	}

	return profits[len(profits)-1][len(profits[0])-1]
}

func Max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```
