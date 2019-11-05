## Question

https://leetcode.com/problems/two-sum/

## Solutions

```go
// O(n) time | O(n) space
func twoSum(nums []int, target int) []int {
	visited := make(map[int]int)

	for i, num := range nums {
		if index, ok := visited[target-num]; ok {
			return []int{index, i}
		}
		visited[num] = i
	}

	return []int{-1, -1}
}
```
