## Solutions

```go
func wordPattern(pattern string, str string) bool {
	words := strings.Split(str, " ")

	if len(pattern) != len(words) {
		return false
	}

	hashMap := make(map[string]string, 0)
	mapValue := make(map[string]bool, 0)

	for i := range words {
		p := string(pattern[i])
		word := words[i]

		if _, ok := hashMap[p]; ok {
			if hashMap[p] != word {
				return false
			}
		} else {
			for v := range mapValue {
				if v == word {
					return false
				}
			}
			hashMap[p] = word
			mapValue[word] = true
		}
	}

	return true
}
```
