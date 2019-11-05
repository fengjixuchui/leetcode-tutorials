## Question

https://leetcode.com/problems/maximum-subarray/

## Solutions

```go
import "math"

// O(n) time | O(1) space
func maxSubArray(nums []int) int {
	var sum int
	maxSum := -math.MaxInt32

	for _, num := range nums {
		if sum < 0 {
			sum = num
		} else {
			sum += num
		}

		if sum > maxSum {
			maxSum = sum
		}
	}

	return maxSum
}
```
