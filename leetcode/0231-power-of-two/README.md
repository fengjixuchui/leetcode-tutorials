## Question

https://leetcode.com/problems/power-of-two/

```go
func isPowerOfTwo(n int) bool {
	// Check if n is negative.
	if n < 0 {
		return false
	}

	// If n is the power of two, then it only has one 1 in it's bit representation.
	count := 0
	for i := 0; i < 32; i++ {
		if n&1 == 1 {
			count++
		}
		if count > 1 {
			return false
		}
		n >>= 1
	}
	return count == 1
}
```
