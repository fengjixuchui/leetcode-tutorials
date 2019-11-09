## Question

https://leetcode.com/problems/maximum-product-subarray/

## Solutions

```go
// O(n) time | O(1) space
func maxProduct(nums []int) int {
	currMax, currMin, max := nums[0], nums[0], nums[0]

	for i := 1; i < len(nums); i++ {
		a := currMax * nums[i]
		b := currMin * nums[i]
		c := nums[i]

		currMax = Max(Max(a, b), c)
		currMin = Min(Min(a, b), c)
		max = Max(currMax, max)
	}

	return max
}

func Min(a, b int) int {
	if a > b {
		return b
	}
	return a
}

func Max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```
