## Question

https://leetcode.com/problems/word-pattern/

## Solutions

```go
// Time: O(n); Space: O(n)
func wordPattern(pattern string, str string) bool {
	strArr := strings.Split(str, " ")

	if len(pattern) != len(strArr) {
		return false
	}

	patternMap := map[byte]string{}
	mappedWord := map[string]bool{}

	for i := 0; i < len(pattern); i++ {
		matchWord, ok := patternMap[pattern[i]]
		if !ok {
			if mapped := mappedWord[strArr[i]]; mapped {
				return false
			}
			patternMap[pattern[i]] = strArr[i]
			mappedWord[strArr[i]] = true
			continue
		}
		if strArr[i] != matchWord {
			return false
		}
	}

	return true
}
```
