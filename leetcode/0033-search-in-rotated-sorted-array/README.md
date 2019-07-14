## Question

https://leetcode.com/problems/search-in-rotated-sorted-array/

## Solutions

```go
func search(nums []int, target int) int {
	if len(nums) == 0 {
		return -1
	}

	l, r := 0, len(nums)-1

	for l <= r {
		m := l + (r-l)/2

		if target == nums[m] {
			return m
		}

		// left sorted
		if nums[l] <= nums[m] {
			// left <= target < mid
			if nums[l] <= target && target < nums[m] {
				r = m - 1
			} else {
				l = m + 1
			}
			// right sorted
		} else {
			// mid < target <= right
			if nums[m] < target && target <= nums[r] {
				l = m + 1
			} else {
				r = m - 1
			}
		}
	}

	return -1
}
```
