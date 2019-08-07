## Question

https://leetcode.com/problems/valid-anagram/

## Solutions

```go
// Time: O(n), Space: O(n)
func isAnagram(s string, t string) bool {
	if len(s) != len(t) {
		return false
	}

	charCount := map[byte]int{}
	for i := 0; i < len(s); i++ {
		charCount[s[i]]++
	}

	for j := 0; j < len(t); j++ {
		if _, ok := charCount[t[j]]; !ok {
			return false
		}
		charCount[t[j]]--
	}

	for _, count := range charCount {
		if count != 0 {
			return false
		}
	}

	return true
}
```
