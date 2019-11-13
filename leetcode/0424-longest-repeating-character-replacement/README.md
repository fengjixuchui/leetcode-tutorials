## Question

https://leetcode.com/problems/longest-repeating-character-replacement/

## Solutions

```go
func characterReplacement(s string, k int) int {
	i, j, maxCount, maxLen := 0, 0, 0, 0
	window := make([]int, 26)

	for j < len(s) {
    idx := s[j] - 'A'
		window[idx]++
		maxCount = max(maxCount, window[idx])
		if (j-i+1)-maxCount > k {
			window[s[i]-'A']--
			i++
		}
		maxLen = max(maxLen, j-i+1)
		j++
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

## Tutorials

- https://www.youtube.com/watch?v=ypEEgP7Hg_I
