## Question

https://leetcode.com/problems/word-break/

## Solutions

```go
// O(n^2) time | O(n+m) space
func wordBreak(s string, wordDict []string) bool {
	n := len(s)
	d := make([]bool, n+1)
	d[0] = true

	set := make(map[string]bool)
	for _, word := range wordDict {
		set[word] = true
	}

	for i := 0; i <= n; i++ {
		for j := i - 1; j >= 0; j-- {
			if set[s[j:i]] {
				if d[j] {
					d[i] = true
					break
				}
			}
		}
	}

	return d[n]
}
```
