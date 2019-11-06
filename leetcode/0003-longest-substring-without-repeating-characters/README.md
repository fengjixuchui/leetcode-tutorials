## Question

https://leetcode.com/problems/longest-substring-without-repeating-characters/

## Solutions

```go
// Time: O(n), Space: O(n)
func lengthOfLongestSubstring(s string) int {
	if len(s) < 2 {
		return len(s)
	}

	visited := make(map[byte]bool)
	var slow, fast, max int

	for fast < len(s) {
		if !visited[s[fast]] {
			visited[s[fast]] = true
			fast++
			if fast-slow > max {
				max = fast - slow
			}
			continue
		}
		visited[s[slow]] = false
		slow++
	}

	return max
}
```
