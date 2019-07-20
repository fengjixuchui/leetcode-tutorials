## Question

https://leetcode.com/problems/0028-implement-strstr/

## Solutions

```go
func strStr(haystack string, needle string) int {
	if len(needle) == 0 {
		return 0
	}

	n, m := len(haystack), len(needle)

	for offset := 0; offset < n-m+1; offset++ {
		for idx := 0; idx < m; idx++ {
			if haystack[offset+idx] != needle[idx] {
				break
			}
			if idx == len(needle)-1 {
				return offset
			}
		}
	}

	return -1
}
```
