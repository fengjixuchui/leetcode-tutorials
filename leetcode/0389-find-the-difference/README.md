## Question

https://leetcode.com/problems/find-the-difference/

## Solutions

```go
func findTheDifference(s string, t string) byte {
	result := t[len(t)-1]
	for i := 0; i < len(s); i++ {
		result = result ^ s[i] ^ t[i]
	}
	return result
}
```
