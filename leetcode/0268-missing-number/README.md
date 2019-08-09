## Question

https://leetcode.com/problems/missing-number/

## Solutions

```go
func missingNumber(nums []int) int {
	if nums == nil || len(nums) == 0 {
		return 0
	}
	missing := len(nums)
	for i := 0; i < len(nums); i++ {
		missing = missing ^ i ^ nums[i]
	}
	return missing
}
```
