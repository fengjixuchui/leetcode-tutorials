## Question

https://leetcode.com/problems/longest-substring-without-repeating-characters/

## Solutions

```go
func lengthOfLongestSubstring(s string) int {
	if len(s) == 0 {
		return 0
	}

	counts := make(map[byte]int, 0)
	maxLen, i, j, n := 0, 0, 0, len(s)

	for ; i < n; i++ {
		for ; j < n; j++ {
			if v := counts[s[j]]; v != 0 {
				break
			}
			counts[s[j]]++
		}
		maxLen = max(maxLen, j-i)
		counts[s[i]]--
	}

	return maxLen
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```
