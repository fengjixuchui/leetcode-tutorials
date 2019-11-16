## Question

https://leetcode.com/problems/insert-interval/

## Solutions

```go
// O(nlogn) time | O(1) space
func insert(intervals [][]int, newInterval []int) [][]int {
	intervals = append(intervals, newInterval)

	sort.Slice(intervals, func(i, j int) bool {
		return intervals[i][0] < intervals[j][0]
	})

	result := [][]int{intervals[0]}

	for i := 1; i < len(intervals); i++ {
		last := result[len(result)-1]
		if last[1] >= intervals[i][0] {
			last[1] = Max(intervals[i][1], last[1])
			continue
		}
		result = append(result, intervals[i])
	}

	return result
}

func Max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```
