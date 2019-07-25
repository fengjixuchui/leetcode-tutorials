## Question

https://leetcode.com/problems/count-primes/

## Solutions

```go
// sieve of eratosthenes
func countPrimes(n int) int {
	if n < 3 {
		return 0
	}

	f := make([]int, n+1)
	for i := 0; i < len(f); i++ {
		f[i] = 1
	}
	f[0], f[1] = 0, 0

	for i := 2; i <= int(math.Sqrt(float64(n))); i++ {
		if f[i] == 0 {
			continue
		}
		for j := i * i; j <= n; j += i {
			f[j] = 0
		}
	}

	count := 0
	// less than the given number
	for i := 0; i < len(f)-1; i++ {
		if f[i] == 1 {
			count++
		}
	}

	return count
}
```
