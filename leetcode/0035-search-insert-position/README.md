## Question

https://leetcode.com/problems/search-insert-position/

## Solutions

```go
func searchInsert(nums []int, target int) int {
    low, high := 0, len(nums) - 1

    for low <= high {
        mid := low + (high - low) / 2

        if nums[mid] == target {
            return mid
        } else if nums[mid] > target {
            high = mid - 1
        } else {
            low = mid + 1
        }
    }

    return low
}
```