## Question

https://leetcode.com/problems/longest-substring-without-repeating-characters/

## Solutions

```go
// Time: O(n), Space: O(n)
func lengthOfLongestSubstring(s string) int {
	if s == "" {
		return 0
	}

	set := map[byte]bool{}
	left, right, max := 0, 0, 0

	for right < len(s) {
		if set[s[right]] == false {
			set[s[right]] = true
			right++
			max = Max(max, right-left)
		} else {
			set[s[left]] = false
			left++
		}
	}

	return max
}

func Max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```
