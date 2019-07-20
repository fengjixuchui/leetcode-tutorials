## Question

https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/

## Solutions

```go
func binarySearchStart(nums []int, target int) int {
	l, r := 0, len(nums)-1

	for l < r {
		m := l + (r-l)/2
		if nums[m] < target {
			l = m + 1
		} else if target < nums[m] {
			r = m
		} else {
			r = m
		}
	}

	return l
}

func binarySearchEnd(nums []int, target int) int {
	l, r := 0, len(nums)-1

	for l < r {
		m := l + (r-l)/2 + 1
		if nums[m] < target {
			l = m
		} else if target < nums[m] {
			r = m - 1
		} else {
			l = m
		}
	}

	return l
}

func searchRange(nums []int, target int) []int {
	if len(nums) == 0 {
		return []int{-1, -1}
	}

	start := binarySearchStart(nums, target)
	if nums[start] != target {
		return []int{-1, -1}
	}

	end := binarySearchEnd(nums, target)
	if nums[end] != target {
		return []int{-1, -1}
	}

	return []int{start, end}
}
```
