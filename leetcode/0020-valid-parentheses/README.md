## Question

https://leetcode.com/problems/0020-valid-parentheses/

## Solutions

```go
// Time: O(n), Space: O(n)
func isValid(s string) bool {
	openPars := map[rune]bool{
		'{': true,
		'[': true,
		'(': true,
	}
	closeOpenParMapping := map[rune]rune{
		'}': '{',
		']': '[',
		')': '(',
	}
	openParStack := []rune{}

	for _, par := range s {
		// Check if the parenthese is an open parenthese.
		if _, ok := openPars[par]; ok {
			openParStack = append(openParStack, par)
			continue
		}

		// Check if the parenthese is one of the close parenthese.
		if _, ok := closeOpenParMapping[par]; !ok {
			return false
		}

		// Check if there's an open parenthesis exists.
		if len(openParStack) == 0 {
			return false
		}

		openPar := closeOpenParMapping[par]
		if openPar != openParStack[len(openParStack)-1] {
			return false
		}
		openParStack = openParStack[:len(openParStack)-1]
	}

	return len(openParStack) == 0
}
```
