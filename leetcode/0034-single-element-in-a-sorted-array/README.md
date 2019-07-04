## Question

https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/

## Solutions

```go
func binarySearchLastOne(nums []int, target int) int {
	left, right := 0, len(nums)-1

	for left <= right {
		mid := left + (right-left)/2
		if target < nums[mid] {
			right--
		} else {
			left++
		}
	}

	return right
}

func searchRange(nums []int, target int) []int {
	if nums == nil || len(nums) == 0 {
		return []int{-1, -1}
	}

	end := binarySearchLastOne(nums, target)
	start := binarySearchLastOne(nums, target-1) + 1

	if 0 <= start && start <= end && end < len(nums) {
		return []int{start, end}
	}

	return []int{-1, -1}
}
```
