## Question

https://leetcode.com/problems/coin-change/

## Solutions

```go
func coinChange(coins []int, amount int) int {
	d := make([][]int, len(coins)+1)
	for i := 0; i < len(d); i++ {
		d[i] = make([]int, amount+1)
	}

	for j := 0; j < len(d[0]); j++ {
		d[0][j] = math.MaxInt32
	}

	for i := 1; i < len(d); i++ {
		for j := 1; j < len(d[0]); j++ {
			useCurCoin := math.MaxInt32
			if j-coins[i-1] >= 0 {
				useCurCoin = d[i][j-coins[i-1]]
			}
			if useCurCoin != math.MaxInt32 {
				useCurCoin++
			}
			d[i][j] = min(d[i-1][j], useCurCoin)
		}
	}

	if d[len(coins)][amount] == math.MaxInt32 {
		return -1
	}
	return d[len(coins)][amount]
}

func min(a, b int) int {
	if a > b {
		return b
	}
	return a
}
```
