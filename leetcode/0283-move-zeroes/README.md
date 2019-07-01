## Question

https://leetcode.com/problems/move-zeroes/

## Solutions

```go
func moveZeroes(nums []int) {
    slow, fast := 0, 0

    for fast < len(nums) {
        if nums[fast] != 0 {
            nums[slow], nums[fast] = nums[fast], nums[slow]
            slow++
        }
        fast++
    }
}
```
