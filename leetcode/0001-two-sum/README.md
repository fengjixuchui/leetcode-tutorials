## Question

https://leetcode.com/problems/two-sum/

## Solutions

```go
func twoSum(nums []int, target int) []int {
	visited := map[int]int{}
	for i := 0; i < len(nums); i++ {
		curNum := nums[i]
		if idx, ok := visited[target-curNum]; ok {
			return []int{idx, i}
		}
		visited[curNum] = i
	}
	return []int{-1, -1}
}
```
