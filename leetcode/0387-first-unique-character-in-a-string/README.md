## Question

https://leetcode.com/problems/first-unique-character-in-a-string/

## Solutions

```go
func firstUniqChar(s string) int {
	d := map[byte]int{}

	// Count each character.
	for i := 0; i < len(s); i++ {
		d[s[i]]++
	}

	// Find the first unique character and return.
	for i := 0; i < len(s); i++ {
		if d[s[i]] == 1 {
			return i
		}
	}

	// If there's no unique character then return -1.
	return -1
}
```
