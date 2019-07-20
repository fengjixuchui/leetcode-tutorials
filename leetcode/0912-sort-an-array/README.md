## Question

https://leetcode.com/problems/sort-an-array/

## Solutions

```go
func quickSort(nums []int, start, end int) {
	if start >= end {
		return
	}

	l, r := start, end
	pivot := nums[l+(r-l)/2]
	for l < r {
		for nums[l] < pivot {
			l++
		}
		for pivot < nums[r] {
			r--
		}
		if l <= r {
			nums[l], nums[r] = nums[r], nums[l]
			l++
			r--
		}
	}

    // In here r is less then l, and l is bigger than r
    // start <= r < l <= end
	quickSort(nums, start, r)
	quickSort(nums, l, end)
}

func sortArray(nums []int) []int {
	if nums == nil {
		return nums
	}
	quickSort(nums, 0, len(nums)-1)
	return nums
}
```
