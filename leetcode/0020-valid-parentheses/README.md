## Question

https://leetcode.com/problems/0020-valid-parentheses/

## Solutions

```go
func isValid(s string) bool {
	stack := make([]rune, 0)

	for i := 0; i < len(s); i++ {
		current := rune(s[i])
		if current == '(' {
			stack = append(stack, ')')
		} else if current == '{' {
			stack = append(stack, '}')
		} else if current == '[' {
			stack = append(stack, ']')
		} else {
			if len(stack) == 0 || (stack[len(stack)-1] != current) {
				return false
			}
			stack = stack[:len(stack)-1]
		}
	}

	return len(stack) == 0
}
```
