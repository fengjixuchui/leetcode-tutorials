## Question

https://leetcode.com/problems/generate-parentheses/

## Solutions

```go
func generateParenthesis(n int) []string {
	results := []string{}
	elem := ""
	dfs(n, n, elem, &results)
	return results
}

func dfs(left int, right int, elem string, results *[]string) {
	if right == 0 && left == 0 {
		*results = append(*results, elem)
		return
	}

	if left > 0 {
		dfs(left-1, right, elem+"(", results)
	}
	if right > left {
		dfs(left, right-1, elem+")", results)
	}
}
```
