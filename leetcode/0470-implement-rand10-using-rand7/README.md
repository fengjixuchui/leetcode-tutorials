## Question

https://leetcode.com/problems/implement-rand10-using-rand7/

## Solutions

```go
func rand10() int {
	x := math.MaxInt32

	for x > 40 {
		x = 7*(rand7()-1) + rand7()
	}

	return x%10 + 1
}
```
