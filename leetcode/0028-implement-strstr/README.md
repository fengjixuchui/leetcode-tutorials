## Question

https://leetcode.com/problems/0028-implement-strstr/

## Solutions

```go
func strStr(haystack string, needle string) int {
	if len(needle) == 0 {
		return 0
	}

	n, m := len(haystack), len(needle)

	for start := 0; start <= n-m; start++ {
		j, k := 0, start
		for j < m && k < n && haystack[k] == needle[j] {
			j++
			k++
		}
		if j == len(needle) {
			return start
		}
	}

	return -1
}
```
