## Question

https://leetcode.com/problems/valid-anagram/

## Solutions

```go
// Time: O(n), Space: O(n)
func isAnagram(s string, t string) bool {
	if len(s) != len(t) {
		return false
	}

	counts := make([]byte, 26)

	for i := 0; i < len(s); i++ {
		counts[s[i]-'a']++
		counts[t[i]-'a']--
	}

	for _, count := range counts {
		if count != 0 {
			return false
		}
	}

	return true
}
```
