## Question

https://leetcode.com/problems/longest-substring-without-repeating-characters/

## Solutions

```go
// Time: O(n), Space: O(n)
func lengthOfLongestSubstring(s string) int {
	if len(s) < 2 {
		return len(s)
	}

	left, right, max := 0, 0, 0
	visited := make(map[byte]bool)

	for right < len(s) {
		char := s[right]
		if !visited[char] {
			visited[char] = true
			max = Max(max, right-left+1)
			right++
		} else {
			char := s[left]
			visited[char] = false
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
