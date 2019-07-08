## Question

https://leetcode.com/problems/product-of-array-except-self/

## Solutions

```go
func productExceptSelf(nums []int) []int {
	n := len(nums)

	leftProduct := make([]int, n, n)
	rightProduct := make([]int, n, n)
	output := make([]int, n, n)

	leftProduct[0] = nums[0]
	rightProduct[n-1] = nums[n-1]

	for i := 1; i < n; i++ {
		leftProduct[i] = leftProduct[i-1] * nums[i]
	}
	for j := n - 2; j >= 0; j-- {
		rightProduct[j] = rightProduct[j+1] * nums[j]
	}

	for i := 0; i < n; i++ {
		if i == 0 {
			output[0] = rightProduct[1]
			continue
		}
		if i == n-1 {
			output[n-1] = leftProduct[n-2]
			continue
		}
		output[i] = leftProduct[i-1] * rightProduct[i+1]
	}

	return output
}
```
