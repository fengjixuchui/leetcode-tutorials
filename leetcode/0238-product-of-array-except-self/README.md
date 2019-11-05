## Question

https://leetcode.com/problems/product-of-array-except-self/

## Solutions

```go
// O(n) time | O(n) space
func productExceptSelf(nums []int) []int {
	n := len(nums)

	leftProducts := make([]int, n)
	rightProducts := make([]int, n)
	result := make([]int, n)

	leftProducts[0] = 1
	rightProducts[len(rightProducts)-1] = 1

	for i := 1; i < n; i++ {
		leftProducts[i] = leftProducts[i-1] * nums[i-1]
	}
	for i := n - 2; i >= 0; i-- {
		rightProducts[i] = rightProducts[i+1] * nums[i+1]
	}

	for i := 0; i < n; i++ {
		result[i] = leftProducts[i] * rightProducts[i]
	}

	return result
}
```
