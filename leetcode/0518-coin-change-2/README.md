## Question

https://leetcode.com/problems/coin-change-2/

## Solutions

```go
func change(amount int, coins []int) int {
	d := make([][]int, len(coins)+1)
	for i := 0; i < len(d); i++ {
		d[i] = make([]int, amount+1)
	}

	for i := 0; i < len(d); i++ {
		d[i][0] = 1
	}

	for i := 1; i < len(d); i++ {
		for j := 1; j < len(d[0]); j++ {
			useCurCoin := 0
			if j-coins[i-1] >= 0 {
				useCurCoin = d[i][j-coins[i-1]]
			} else {
				useCurCoin = 0
			}
			d[i][j] = d[i-1][j] + useCurCoin
		}
	}

	return d[len(coins)][amount]
}
```
