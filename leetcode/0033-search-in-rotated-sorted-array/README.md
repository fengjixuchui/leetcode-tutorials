## Question

https://leetcode.com/problems/search-in-rotated-sorted-array/

## Solutions

```go
// Time: O(logn), Space: O(1)
func search(nums []int, target int) int {
	if nums == nil || len(nums) == 0 {
		return -1
	}

	l, r := 0, len(nums)-1

	for l <= r {
		m := l + (r-l)/2

		if nums[m] == target {
			return m
		}

		if nums[m] < nums[r] {
			// right part is ascending
			if nums[m] < target && target <= nums[r] {
				l = m + 1
			} else {
				r = m - 1
			}
		} else {
			// left part is ascending
			if nums[l] <= target && target < nums[m] {
				r = m - 1
			} else {
				l = m + 1
			}
		}
	}

	return -1
}
```
