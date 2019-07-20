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

### binarySearchStart

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
```

### binarySearchEnd

```go
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
```
