## Question

https://leetcode.com/problems/shortest-unsorted-continuous-subarray/

## Solutions

```go
func findUnsortedSubarray(nums []int) int {
	i, j, n, max, min := 0, -1, len(nums), math.MinInt32, math.MaxInt32

	for k := 0; k < n; k++ {
		max = Max(max, nums[k])
		if nums[k] != max {
			j = k
		}
	}
	for k := n - 1; k >= 0; k-- {
		min = Min(min, nums[k])
		if nums[k] != min {
			i = k
		}
	}

	return j - i + 1
}

func Max(a, b int) int {
	if a > b {
		return a
	}
	return b
}

func Min(a, b int) int {
	if a > b {
		return b
	}
	return a
}
```
