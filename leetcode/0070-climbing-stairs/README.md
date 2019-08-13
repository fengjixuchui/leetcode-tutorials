## Question

https://leetcode.com/problems/0070-climbing-stairs/

## Solutions

```go
// Time: O(n), Space: O(n)
func climbStairs(n int) int {
	ways := make([]int, n+1)
	ways[0] = 1
	ways[1] = 1

	for i := 2; i <= n; i++ {
		ways[i] = ways[i-1] + ways[i-2]
	}

	return ways[n]
}
```
