## Question

https://leetcode.com/problems/palindrome-partitioning/

## Solutions

```go
func partition(s string) [][]string {
	ans := [][]string{}
	bt(&ans, []string{}, 0, s)
	return ans
}

func bt(ans *[][]string, cur []string, offset int, s string) {
	if offset == len(s) {
		t := make([]string, len(cur))
		copy(t, cur)
		*ans = append(*ans, t)
		return
	}

	for i := offset; i < len(s); i++ {
		subStr := s[offset : i+1]
		if isPalindrome(subStr) {
			t := make([]string, len(cur))
			copy(t, cur)
			t = append(t, subStr)
			bt(ans, t, i+1, s)
		}
	}
}

func isPalindrome(s string) bool {
	l := len(s)
	for i, j := 0, l-1; i < j; i, j = i+1, j-1 {
		if s[i] != s[j] {
			return false
		}
	}
	return true
}
```
