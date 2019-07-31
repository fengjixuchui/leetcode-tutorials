## Question

https://leetcode.com/problems/search-insert-position/

## Solutions

```go
func searchInsert(nums []int, target int) int {
	if nums == nil || len(nums) == 0 {
		return -1
	}

	l, r := 0, len(nums)-1

	for l+1 < r {
		m := l + (r-l)/2
		if nums[m] == target {
			return m
		} else if nums[m] < target {
			l = m
		} else {
			r = m
		}
	}

	if nums[r] < target {
		return r + 1
	} else if target <= nums[l] {
		return l
	} else {
		return r
	}
}
```
