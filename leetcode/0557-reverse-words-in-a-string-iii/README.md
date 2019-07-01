## Question

https://leetcode.com/problems/reverse-words-in-a-string-iii/

## Solutions

```go
func reverseWords(s string) string {
	start, end := 0, 0
	c := []byte(s)
	n := len(s)

	for start < n {
		for end < n && c[end] != ' ' {
			end++
		}
		for i, j := start, end-1; i < j; {
			c[i], c[j] = c[j], c[i]
			i++
			j--
		}
		start = end + 1
		end = start
	}

	return string(c)
}
```
