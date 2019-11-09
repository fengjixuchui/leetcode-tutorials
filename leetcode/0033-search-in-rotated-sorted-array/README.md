## Question

https://leetcode.com/problems/search-in-rotated-sorted-array/

## Solutions

```go
func search(nums []int, target int) int {
	if len(nums) == 0 {
		return -1
	}

	l, r := 0, len(nums)-1

	for l+1 < r {
		m := l + (r-l)/2

		if nums[m] == target {
			return m
		}
		// Right sorted
		if nums[m] < nums[r] {
			if nums[m] < target && target <= nums[r] {
				l = m + 1
			} else {
				r = m - 1
			}
		} else {
			if nums[l] <= target && target < nums[m] {
				r = m - 1
			} else {
				l = m + 1
			}
		}
	}

	if nums[l] == target {
		return l
	} else if nums[r] == target {
		return r
	} else {
		return -1
	}
}
```
