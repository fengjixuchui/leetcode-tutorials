## Question

https://leetcode.com/problems/valid-perfect-square/

## Solutions

```go
func isPerfectSquare(num int) bool {
	if num == 1 {
		return true
	}

	l, r := 0, num

	for l < r {
		m := l + (r-l)/2
		if m*m < num {
			l = m + 1
		} else if m*m > num {
			r = m
		} else {
			return true
		}
	}

	return false
}
```
