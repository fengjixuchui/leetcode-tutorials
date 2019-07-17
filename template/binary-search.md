## Binary Search

### Basic

```go
func bs(nums []int, target) int {
	l, r := 0, len(nums)-1

	for l < r {
		m := l + (r-1)/2
		if nums[m] < target {
			l = m + 1
		} else if nums[m] > target {
			r = m
		} else {
			return m
		}
	}

	return -1
}
```
