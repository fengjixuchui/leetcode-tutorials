## Question

https://leetcode.com/problems/valid-palindrome/

## Solutions

```go
func isAlphaNum(c byte) bool {
	return ('a' <= c && c <= 'z') || ('A' <= c && c <= 'Z') || ('0' <= c && c <= '9')
}

func isPalindrome(s string) bool {
	left, right := 0, len(s)-1

	for left < right {
		for left < right && !isAlphaNum(s[left]) {
			left++
		}
		for left < right && !isAlphaNum(s[right]) {
			right--
		}
		if strings.ToLower(string(s[left])) != strings.ToLower(string(s[right])) {
			return false
		}
		left++
		right--
	}

	return true
}
```
