## Question

https://leetcode.com/problems/longest-palindromic-substring/

## Solutions

```go
func expand(s string, left int, right int) string {
	for left >= 0 && right < len(s) && s[left] == s[right] {
		left--
		right++
	}
	return s[left+1 : right]
}

func longestPalindrome(s string) string {
	if s == "" {
		return ""
	}

	longest := ""

	for i := 0; i < len(s); i++ {
		len1 := expand(s, i, i)
		if len(len1) > len(longest) {
			longest = len1
		}
		len2 := expand(s, i, i+1)
		if len(len2) > len(longest) {
			longest = len2
		}
	}

	return longest
}
```
