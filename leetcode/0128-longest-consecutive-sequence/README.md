## Question

https://leetcode.com/problems/longest-consecutive-sequence/

## Solutions

```go
import "sort"

func longestConsecutive(nums []int) int {
	if nums == nil || len(nums) == 0 {
		return 0
	}

	sort.Ints(nums)
	max, p := 0, 0

	for p < len(nums) {
		count := 1
		for p < len(nums)-1 {
			if nums[p+1]-nums[p] > 1 {
				break
			}
			if nums[p+1]-nums[p] == 1 {
				count++
			}
			p++
		}
		max = Max(max, count)
		p++
	}

	return max
}

func Max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```
