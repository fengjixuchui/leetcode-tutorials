## Question

https://leetcode.com/problems/reverse-string/

## Solutions

```go
func reverseString(s []byte) {
	left, right := 0, len(s)-1

	for left < right {
		s[left], s[right] = s[right], s[left]
		left++
		right--
	}
}
```