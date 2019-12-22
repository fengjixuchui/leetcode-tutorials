## Question

https://leetcode.com/problems/binary-search/

## Solutions

```go
func search(nums []int, target int) int {
	if nums == nil || len(nums) == 0 {
		return -1
	}

	l, r := 0, len(nums)-1

	for l+1 < r {
		m := l + (r-l)/2
		if nums[m] == target {
			return m
		}
		if nums[m] < target {
			l = m
		} else {
			r = m
		}
	}

	if nums[l] == target {
		return l
	}
	if nums[r] == target {
		return r
	}

	return -1
}
```
