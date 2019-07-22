## Question

https://leetcode.com/problems/base-7/

## Solutions

```go
func convertToBase7(num int) string {
	neg := false

	if num < 0 {
		neg = true
		num = -num
	}

	ans := ""

	for {
		ans = strconv.Itoa(num%7) + ans
		num /= 7
		if num == 0 {
			break
		}
	}

	if neg {
		ans = "-" + ans
	}
	return ans
}
```
