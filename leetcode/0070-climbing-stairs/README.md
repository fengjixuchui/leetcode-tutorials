## Question

https://leetcode.com/problems/climbing-stairs/

## Solutions

```go
// Time: O(n), Space: O(n)
func climbStairs(n int) int {
	d := make([]int, n+1)

	d[0] = 1
	d[1] = 1

	for i := 2; i <= n; i++ {
		d[i] = d[i-2] + d[i-1]
	}

	return d[n]
}
```
