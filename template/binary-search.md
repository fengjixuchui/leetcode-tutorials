## Binary Search

### Basic

```go
func bs(nums []int, target) int {
	l, r := 0, len(nums)-1

	for l < r {
		mid := l + (r-1)/2
		if nums[mid] < target {
			l = mid + 1
		} else if nums[mid] > target {
			r = mid + 1
		} else {
			return mid
		}
	}

	return -1
}
```
