## Question

https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/

## Solutions

```go
// O(logn) time | O(1) space
func findMin(nums []int) int {
	if nums == nil || len(nums) == 0 {
		return 0
	}

	left, right := 0, len(nums)-1

	// Sorted
	if nums[left] < nums[right] {
		return nums[left]
	}

	for left+1 < right {
		mid := left + (right-left)/2
		if nums[mid] < nums[right] {
			right = mid
		} else {
			left = mid
		}
	}

	if nums[left] < nums[right] {
		return nums[left]
	}
	return nums[right]
}
```
