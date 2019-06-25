## Solutions

```go
func twoSum(nums []int, target int) []int {
	// visited store value and index
	visited := make(map[int]int)

	for currentIndex, v := range nums {
		counterPart := target - v

		counterPartIndex, ok := visited[counterPart]
		if ok {
			return []int{counterPartIndex, currentIndex}
		}
		visited[v] = currentIndex
	}

	return []int{-1, -1}
}
```
