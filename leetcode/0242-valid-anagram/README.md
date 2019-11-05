## Question

https://leetcode.com/problems/valid-anagram/

## Solutions

```go
// Time: O(n), Space: O(n)
func isAnagram(s string, t string) bool {
	if len(s) != len(t) {
		return false
	}

	runeCount := make(map[rune]int)

	for _, r := range s {
		runeCount[r]++
	}

	for _, r := range t {
		count, ok := runeCount[r]
		if count == 0 || !ok {
			return false
		}
		runeCount[r]--
	}

	for _, value := range runeCount {
		if value != 0 {
			return false
		}
	}

	return true
}
```
