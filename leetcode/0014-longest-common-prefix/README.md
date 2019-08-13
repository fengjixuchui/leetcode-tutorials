## Question

https://leetcode.com/problems/longest-common-prefix/

## Solutions

```go
func longestCommonPrefix(strs []string) string {
	longestCommonPrefix := ""

	if strs == nil || len(strs) == 0 {
		return longestCommonPrefix
	}

	for i := 0; i < len(strs[0]); i++ {
		char := strs[0][i]
		for j := 1; j < len(strs); j++ {
			if i > len(strs[j])-1 || strs[j][i] != char {
				return longestCommonPrefix
			}
		}
		longestCommonPrefix += string(char)
	}

	return longestCommonPrefix
}
```
