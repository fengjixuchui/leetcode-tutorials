## Question

https://leetcode.com/problems/valid-palindrome/

## Solutions

```go
// Time: O(n), Space: O(1)
func isPalindrome(s string) bool {
	if len(s) == 0 {
		return true
	}

	s = strings.ToLower(s)

	l, r := 0, len(s)-1

	for l < r {
		for l < r && !isValid(s[l]) {
			l++
		}
		for l < r && !isValid(s[r]) {
			r--
		}
		if s[l] != s[r] {
			return false
		}
		l++
		r--
	}

	return true
}

func isValid(char byte) bool {
	return ('a' <= char && char <= 'z') || ('0' <= char && char <= '9')
}
```

## Tutorials

- https://www.youtube.com/watch?v=3RQ5ADUKHsY
