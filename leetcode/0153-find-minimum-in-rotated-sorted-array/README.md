## Question

https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/

## Solutions

```go
func findMin(nums []int) int {
	if nums == nil || len(nums) == 0 {
		return -1
	}

	l, r := 0, len(nums)-1
	for l+1 < r {
		// sorted
		if nums[l] < nums[r] {
			return nums[l]
		}

		m := l + (r-l)/2

		if nums[m] > nums[r] {
			l = m
		} else {
			r = m
		}
	}

	if nums[l] > nums[r] {
		return nums[r]
	}
	return nums[l]
}
```
