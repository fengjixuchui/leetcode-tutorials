## Question

https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/

## Solutions

```go
func findStart(nums []int, target int) int {
	l, r := 0, len(nums)-1

	for l+1 < r {
		m := l + (r-l)/2
		if nums[m] == target {
			r = m
		} else if nums[m] < target {
			l = m
		} else {
			r = m
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

func findEnd(nums []int, target int) int {
	l, r := 0, len(nums)-1

	for l+1 < r {
		m := l + (r-l)/2
		if nums[m] == target {
			l = m
		} else if nums[m] < target {
			l = m
		} else {
			r = m
		}
	}

	if nums[r] == target {
		return r
	} else if nums[l] == target {
		return l
	} else {
		return -1
	}
}

func searchRange(nums []int, target int) []int {
	if nums == nil || len(nums) == 0 {
		return []int{-1, -1}
	}
	start := findStart(nums, target)
	end := findEnd(nums, target)
	return []int{start, end}
}
```
