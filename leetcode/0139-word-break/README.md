## Question

https://leetcode.com/problems/word-break/

## Solutions

```go
func wordBreak(s string, wordDict []string) bool {
	n := len(s)
	d := make([]bool, n+1)
	d[0] = true

	for i := 0; i <= n; i++ {
		for j := i - 1; j >= 0; j-- {
			if d[j] && contains(wordDict, s[j:i]) {
				d[i] = true
				break
			}
		}
	}

	return d[n]
}

func contains(s []string, e string) bool {
	for _, a := range s {
		if a == e {
			return true
		}
	}
	return false
}
```
