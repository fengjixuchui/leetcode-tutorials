## Question

https://leetcode.com/problems/search-in-rotated-sorted-array-ii/

## Solutions

```go
func search(nums []int, target int) bool {
	if nums == nil || len(nums) == 0 {
		return false
	}

	l, r := 0, len(nums)-1

	for l <= r {
		m := l + (r-l)/2

		if nums[m] == target {
			return true
		}

		// right sorted
		if nums[m] < nums[l] {
			if nums[m] < target && target <= nums[r] {
				l = m + 1
			} else {
				r = m - 1
			}
			// left sorted
		} else if nums[l] < nums[m] {
			if nums[l] <= target && target < nums[m] {
				r = m - 1
			} else {
				l = m + 1
			}
		} else {
			l++
		}
	}

	return false
}
```
