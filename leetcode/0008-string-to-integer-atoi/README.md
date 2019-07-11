## Question

https://leetcode.com/problems/string-to-integer-atoi/

## Solutions

```go
func myAtoi(str string) int {
	start, p, n, sign := 0, 0, len(str), 1

	// Skip leading spaces
	for p < n && str[p] == ' ' {
		p++
	}
	if p == n {
		return 0
	}

	// +/- Sign
	if str[p] == '+' {
		p++
	} else if str[p] == '-' {
		p++
		sign = -1
	}

	for p < n && str[p] == '0' {
		p++
	}

	start = p
	for p < n && str[p] >= '0' && str[p] <= '9' {
		p++
	}
	if p == start {
		return 0
	}

	num := 0
	for i := start; i < p; i++ {
		num = num*10 + int(str[i]-'0')
		if num*sign > math.MaxInt32 {
			return math.MaxInt32
		} else if num*sign < math.MinInt32 {
			return math.MinInt32
		}
	}

	return num * sign
}
```
