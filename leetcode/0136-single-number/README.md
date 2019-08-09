## Question

https://leetcode.com/problems/single-number/

## Solutions

```go
func singleNumber(nums []int) int {
	if nums == nil || len(nums) == 0 {
		return 0
	}

	result := 0
	for i := 0; i < len(nums); i++ {
		result ^= nums[i]
	}
	return result
}
```
