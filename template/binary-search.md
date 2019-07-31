## Binary Search

### Classic

```go
func bs(nums []int, target int) int {
	l, r := 0, len(nums)-1

	for l <= r {
		m := l + (r-1)/2
		if nums[m] < target {
			l = m + 1
		} else if nums[m] > target {
			r = m - 1
		} else {
			return m
		}
	}

	return -1
}
```

### Super useful

```go
func searchInsert(nums []int, target int) int {
	if nums == nil || len(nums) == 0 {
		return -1
	}

	l, r := 0, len(nums)-1

	// r - l > 1, so that we can avoid edge case.
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

	// Check the rest two elements.
	if nums[r] < target {
		return r + 1
	} else if target <= nums[l] {
		return l
	} else {
		return r
	}
}
```
