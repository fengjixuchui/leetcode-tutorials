## Question

https://leetcode.com/problems/069-sqrtx/

## Solutions

```go
func mySqrt(x int) int {
	l, r := 0, x

	for l+1 < r {
		m := l + (r-l)/2
		if m*m < x {
			l = m
		} else if m*m > x {
			r = m
		} else {
			return m
		}
	}

	if l*l == x {
		return l
	} else if r*r == x {
		return r
	} else {
		return l
	}
}
```
