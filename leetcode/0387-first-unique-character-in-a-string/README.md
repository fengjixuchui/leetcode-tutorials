## Question

https://leetcode.com/problems/first-unique-character-in-a-string/

## Solutions

```go
func firstUniqChar(s string) int {
	if s == "" {
		return -1
	}

	arr := make([]int, 26)
	for _, r := range s {
		arr[r-'a']++
	}
	for i, r := range s {
		if arr[r-'a'] == 1 {
			return i
		}
	}

	return -1
}
```
