## Question

https://leetcode.com/problems/kth-largest-element-in-an-array

## Solutions

```go
import "sort"

func findKthLargest(nums []int, k int) int {
	sort.Ints(nums)
	return nums[len(nums)-k]
}
```
