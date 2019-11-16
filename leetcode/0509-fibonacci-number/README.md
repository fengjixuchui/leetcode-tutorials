## Question

https://leetcode.com/problems/fibonacci-number/

## Solutions

```go
// Time: O(2^n), Space: O(1)
func fib(n int) int {
	if n == 0 {
		return 0
	}
	if n == 1 {
		return 1
	}
	return fib(n-1) + fib(n-2)
}
```


```go
func fib(N int) int {
	if N <= 0 {
		return 0
	}
	if N == 1 {
		return 1
	}

	d := make([]int, N+1)
	d[0] = 0
	d[1] = 1

	for i := 2; i <= N; i++ {
		d[i] = d[i-1] + d[i-2]
	}

	return d[N]
}
```

```go
var dp = map[int]int{0: 0, 1: 1}

func fib(N int) int {
	if N == 0 {
		return 0
	}
	if N == 1 {
		return 1
	}

	if value, ok := dp[N]; ok {
		return value
	}

	dp[N] = fib(N-1) + fib(N-2)

	return dp[N]
}
```
