## Question

https://leetcode.com/problems/longest-palindrome/

## Solutions

```go
func longestPalindrome(s string) int {
	d := make([]int, 256, 256)
	oddNum := 0
	for _, c := range s {
		d[c]++
	}
	for _, count := range d {
		if count%2 == 1 {
			oddNum++
		}
	}

	unUsed := 0
	if oddNum-1 > 0 {
		unUsed = oddNum - 1
	}

	return len(s) - unUsed
}
```
