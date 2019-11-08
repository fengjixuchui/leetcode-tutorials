## Question

https://leetcode.com/problems/merge-intervals/

## Solutions

```go
// O(nlogn) time | O(1) space
func merge(intervals [][]int) [][]int {
	if len(intervals) < 2 {
		return intervals
	}

	// sorting: O(nlogn)
	sort.Slice(intervals, func(i, j int) bool {
		return intervals[i][0] < intervals[j][0]
	})

	result := [][]int{intervals[0]}

	for i := 1; i < len(intervals); i++ {
		lastI := result[len(result)-1]
		// lastI[1] > intervals[i][0] means that there's an overlap.
		if lastI[1] >= intervals[i][0] {
			if lastI[1] > intervals[i][1] {
				continue
			} else {
				lastI[1] = intervals[i][1]
			}
		} else {
			result = append(result, intervals[i])
		}
	}

	return result
}
```
