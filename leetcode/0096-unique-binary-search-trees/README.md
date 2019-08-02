## Question

https://leetcode.com/problems/unique-binary-search-trees/

## Solutions

```go
func numTrees(n int) int {
	if n < 0 {
		return 0
	}
	d := make([]int, n+1)
	d[0] = 1
	for i := 1; i <= n; i++ {
		for j := 1; j <= i; j++ {
			// d[j-1] left
			// d[i-j] right
			d[i] += d[j-1] * d[i-j]
		}
	}
	return d[n]
}
```
