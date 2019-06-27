## Question

https://leetcode.com/problems/0392-is-subsequence/

## Solutions

```go
func isSubsequence(s string, t string) bool {
	if len(s) == 0 {
		return true
	}

	curIndex := 0

	for i := 0; i < len(t); i++ {
		if t[i] == s[curIndex] {
			curIndex++
		}
		if curIndex == len(s) {
			return true
		}
	}

	return false
}
```
