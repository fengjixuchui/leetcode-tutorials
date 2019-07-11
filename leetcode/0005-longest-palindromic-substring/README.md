## Question

https://leetcode.com/problems/longest-palindromic-substring/

## Solutions

```go
func longestPalindrome(s string) string {
	if len(s) == 0 {
		return s
	}

	start, n, maxLen := 0, len(s), 0
	d := make([][]bool, n)
	for i := 0; i < n; i++ {
		d[i] = make([]bool, n)
	}

	for i := n - 1; i >= 0; i-- {
		for j := i; j < n; j++ {
			if i == j {
				d[i][j] = true
			} else if i+1 == j {
				d[i][j] = s[i] == s[j]
			} else {
				d[i][j] = s[i] == s[j] && d[i+1][j-1]
			}

			if d[i][j] && (j-i+1) > maxLen {
				start = i
				maxLen = j - i + 1
			}
		}
	}

	return s[start : start+maxLen]
}
```
