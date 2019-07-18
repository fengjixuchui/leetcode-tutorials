## Question

https://leetcode.com/problems/perfect-squares/

## Solutions

```go
func numSquares(n int) int {
	d := make([]int, n+1)
	d[0] = 0

	for i := 1; i <= n; i++ {
		// if all use 1
		d[i] = i
		for j := 1; j*j <= i; j++ {
			d[i] = Min(d[i], d[i-j*j]+1)
		}
	}

	return d[n]
}

func Min(a, b int) int {
	if a > b {
		return b
	}
	return a
}
```
