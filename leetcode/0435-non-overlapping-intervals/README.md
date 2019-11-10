## Question

https://leetcode.com/problems/non-overlapping-intervals/

## Solutions

```go
// O(n) time | O(1) space
func eraseOverlapIntervals(intervals [][]int) int {
	if len(intervals) == 0 {
		return 0
	}

	sort.Slice(intervals, func(i, j int) bool {
		return intervals[i][1] < intervals[j][1]
	})

	intervalsRemoved := 0
	lastValidintervalIndex := 0

	for i := 1; i < len(intervals); i++ {
		// overlapping
		if intervals[lastValidintervalIndex][1] > intervals[i][0] {
			intervalsRemoved++
		} else {
			lastValidintervalIndex = i
		}
	}

	return intervalsRemoved
}
```
