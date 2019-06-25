## Solutions

```go
func reverseVowels(s string) string {
	vowels := "aeiouAEIOU"
	left, right := 0, len(s)-1

	ss := []rune(s)

	for left < right {
		if !strings.ContainsRune(vowels, ss[left]) {
			left++
		} else if !strings.ContainsRune(vowels, ss[right]) {
			right--
		} else {
			ss[left], ss[right] = ss[right], ss[left]
			left++
			right--
		}
	}

	return string(ss)
}
```
