## Question

https://leetcode.com/problems/minimum-window-substring/

## Solutions

```go
// O(n) time | O(1) space
func minWindow(s string, t string) string {
	l, r, count, minLen, res := 0, 0, 0, math.MaxInt32, ""
	lookup := make([]int, 128)

	for i := 0; i < len(t); i++ {
		lookup[t[i]]++
	}

	for r < len(s) {
		lookup[s[r]]--
		if lookup[s[r]] >= 0 {
			count++
		}
		for count == len(t) {
			if minLen > r-l+1 {
				minLen = r - l + 1
				res = s[l : r+1]
			}
			lookup[s[l]]++
			if lookup[s[l]] > 0 {
				count--
			}
			l++
		}
		r++
	}

	return res
}
```

## Tutorials

- https://www.youtube.com/watch?v=0GOyCIJ2ajQ
