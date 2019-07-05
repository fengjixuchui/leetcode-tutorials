## Question

https://leetcode.com/problems/validate-stack-sequences/

## Solutions

```go
func validateStackSequences(pushed []int, popped []int) bool {
	stack := make([]int, 0)

	for i := 0; i < len(pushed); i++ {
		stack = append(stack, pushed[i])
		for len(popped) != 0 && len(stack) != 0 && popped[0] == stack[len(stack)-1] {
			stack = stack[:len(stack)-1]
			popped = popped[1:]
		}
	}

	return len(stack) == 0
}
```
