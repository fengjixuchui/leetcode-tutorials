## Question

https://leetcode.com/problems/valid-anagram/

## Solutions

```go
func isAnagram(s string, t string) bool {
	hashMap := map[rune]int{}

	for _, char := range s {
		hashMap[char]++
	}

	for _, char := range t {
		if _, ok := hashMap[char]; !ok {
			return false
		}
		hashMap[char]--
	}

	for _, count := range hashMap {
		if count != 0 {
			return false
		}
	}

	return true
}
```
