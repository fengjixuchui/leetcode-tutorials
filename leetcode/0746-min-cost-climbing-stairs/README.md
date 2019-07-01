## Question

https://leetcode.com/problems/min-cost-climbing-stairs/

## Solutions

```go
func minCostClimbingStairs(cost []int) int {
  n := len(cost)
	d := make([]int, n, n)
	d[0], d[1] = cost[0], cost[1]
	for i := 2; i < n; i++ {
		d[i] = min(d[i-2], d[i-1]) + cost[i]
	}
  fmt.Printf("d %+v", d)
  return min(d[n-1], d[n-2])
}

func min(a, b int) int {
	if a > b {
		return b
	}
	return a
}
```
