## Question

https://leetcode.com/problems/single-number/

## Solutions

```go
func singleNumber(nums []int) int {
	result := 0
	for _, v := range nums {
		result ^= v
	}
	return result
}
```
