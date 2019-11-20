## Question

https://leetcode.com/problems/valid-parentheses/

## Solutions

```go
// T: O(n), S: O(n)
func isValid(s string) bool {
	stack := []rune{}
	mapping := map[rune]rune{
		')': '(',
		']': '[',
		'}': '{',
	}

	for _, char := range s {
		pair, ok := mapping[char]
		// is an open pair
		if !ok {
			stack = append(stack, char)
		} else {
			// is a close pair
			if len(stack) == 0 {
				return false
			}

			// pop from the stack
			openPair := stack[len(stack)-1]
			stack = stack[:len(stack)-1]

			if pair != openPair {
				return false
			}
		}
	}

	return len(stack) == 0
}
```
