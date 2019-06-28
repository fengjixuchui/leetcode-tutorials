## Question

https://leetcode.com/problems/0268-missing-number/

## Solutions

```go
func missingNumber(nums []int) int {
	missing := len(nums)
	for i, v := range nums {
		missing = missing ^ i ^ v
	}
	return missing
}
```
