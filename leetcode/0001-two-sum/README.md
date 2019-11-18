## Question

https://leetcode.com/problems/two-sum/

## Solutions

```go
// O(n^2) time | O(1) space
func twoSum(nums []int, target int) []int {
	for i := 0; i < len(nums); i++ {
		for j := i + 1; j < len(nums); j++ {
			sum := nums[i] + nums[j]
			if sum == target {
				return []int{i, j}
			}
		}
	}
	return []int{-1, -1}
}

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
