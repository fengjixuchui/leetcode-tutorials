## Question

https://leetcode.com/problems/remove-invalid-parentheses/

## Solutions

```go
func removeInvalidParentheses(s string) []string {
	l, r := 0, 0

	for i := 0; i < len(s); i++ {
		ch := s[i]

		if ch == '(' {
			l++
		}

		if l == 0 {
			if ch == ')' {
				r++
			}
		} else {
			if ch == ')' {
				l--
			}
		}
	}

	ans := make([]string, 0)
	dfs(s, 0, l, r, &ans)
	return ans
}

func isValid(s string) bool {
	count := 0
	for i := 0; i < len(s); i++ {
		if s[i] == '(' {
			count++
		} else if s[i] == ')' {
			count--
		}
		if count < 0 {
			return false
		}
	}
	return count == 0
}

func dfs(s string, start int, l int, r int, ans *[]string) {
	if l == 0 && r == 0 {
		if isValid(s) {
			*ans = append(*ans, s)
			return
		}
	}

	for i := start; i < len(s); i++ {
		if i != start && s[i] == s[i-1] {
			continue
		}

		if s[i] == '(' {
			dfs(s[:i]+s[i+1:], i, l-1, r, ans)
		} else if s[i] == ')' {
			dfs(s[:i]+s[i+1:], i, l, r-1, ans)
		}
	}
}
```
