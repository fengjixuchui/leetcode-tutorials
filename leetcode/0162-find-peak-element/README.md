## Question

https://leetcode.com/problems/find-peak-element/

## Solutions

```go
func findPeakElement(nums []int) int {
	if nums == nil || len(nums) == 0 {
		return -1
	}

	l, r := 0, len(nums)-1

	for l+1 < r {
		m := l + (r-l)/2
		if nums[m] < nums[m+1] {
			l = m
		} else {
			r = m
		}
	}

	if nums[l] < nums[r] {
		return r
	}
	return l
}
```
