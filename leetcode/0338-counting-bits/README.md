## Question

https://leetcode.com/problems/counting-bits/

## Solutions

```go
func countBits(n int) []int {
	d := make([]int, n+1)
	for i := 1; i <= n; i++ {
		d[i] = d[i>>1] + i&1
	}
	return d
}
```
