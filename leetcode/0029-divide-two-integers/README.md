## Question

https://leetcode.com/problems/divide-two-integers/

## Solutions

```go
// Time: O(logn), Space: O(1)
func divide(dividend int, divisor int) int {
	if dividend == math.MinInt32 && divisor == -1  {
        return math.MaxInt32
	}

	sign := 1

	if dividend < 0 {
		dividend = -dividend
		sign = -sign
	}
	if divisor < 0 {
		divisor = -divisor
		sign = -sign
	}

	res := 0
	for dividend >= divisor {
		var shift uint
		for dividend >= divisor<<shift {
			shift++
		}
		res += 1 << (shift - 1)
		dividend -= divisor << (shift - 1)
	}

	return sign * res
}

```
