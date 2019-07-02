## Question

https://leetcode.com/problems/generate-parentheses/

## Solutions

```go
func generateParenthesis(n int) []string {
    if n <= 0 {
        return []string{}
    }
    result := make([]string, 0)
    generate(&result, "", n, n)
    return result
}

func generate(result *[]string, str string, left int, right int) {
    if left == 0 && right == 0 {
        *result = append(*result, str)
    } else {
        if left > 0 {
            generate(result, str + "(", left - 1, right)
        }
        if right > left {
            generate(result, str + ")", left, right - 1)
        }
    }
}
```
