## Question

https://leetcode.com/problems/fibonacci-number/

## Solutions

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
