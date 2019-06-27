## Question

https://leetcode.com/problems/maximum-subarray/

## Solutions

```go
func maxSubArray(nums []int) int {
	cur, max := nums[0], nums[0]
	for _, v := range(nums[1:]) {
        if cur < 0 {
            cur = v
        } else {
            cur += v
        }
        if cur > max {
            max = cur
        }
    }
    return max
}
```
