## Solutions

```go
func isPowerOfThree(n int) bool {
	if n == 1 {
		return true
	}

	if n < 2 {
		return false
	}

	for n >= 3 {
		if n%3 == 0 {
			n = n / 3
		} else {
			return false
		}
	}

	return n == 1
}
```
