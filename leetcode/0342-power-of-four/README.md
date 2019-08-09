## Solutions

```go
// If the number is the power of four
// then then number must have one 1 and it's in the even position.
func isPowerOfFour(num int) bool {
	// Count the number of 1.
	count := 0
	for i := 0; i < 32; i++ {
		// Check the last digit.
		if (num & 1) == 1 {
			// If the 1 is not in the even position then it's not the power of four.
			if i%2 != 0 {
				return false
			}
			count++
		}
		if count > 1 {
			return false
		}
		num >>= 1
	}

	return count == 1
}
```
