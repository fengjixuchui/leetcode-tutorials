## Question

https://leetcode.com/problems/contains-duplicate/

```go
// O(n) time | O(n) space
func containsDuplicate(nums []int) bool {
	visited := make(map[int]bool)

	for _, num := range nums {
		if _, ok := visited[num]; ok {
			return true
		}
		visited[num] = true
	}

	return false
}
```
