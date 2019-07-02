## Question

https://leetcode.com/problems/merge-intervals/

## Solutions

```go
func merge(intervals []Interval) []Interval {
	if len(intervals) == 0 {
		return nil
	}

	sort.Slice(intervals, func(i, j int) bool {
		return intervals[i].Start < intervals[j].Start
	})

	var result []Interval
	cur := intervals[0]
	for i := 1; i < len(intervals); i++ {
		check := intervals[i]
		if cur.End >= check.Start {
			cur.End = max(cur.End, check.End)
		} else {
			result = append(result, cur)
			cur = check
		}
	}
	result = append(result, cur)
	return result
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```
