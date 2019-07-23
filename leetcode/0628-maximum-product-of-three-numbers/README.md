## Question

https://leetcode.com/problems/maximum-product-of-three-numbers/

## Solutions

```go
func maximumProduct(nums []int) int {
	max1 := math.MinInt32
	max2 := math.MinInt32
	max3 := math.MinInt32
	min1 := math.MaxInt32
	min2 := math.MaxInt32

	for i := 0; i < len(nums); i++ {
		if nums[i] > max1 {
			max1, max2, max3 = nums[i], max1, max2
		} else if nums[i] > max2 {
			max2, max3 = nums[i], max2
		} else if nums[i] > max3 {
			max3 = nums[i]
		}

		if nums[i] < min1 {
			min1, min2 = nums[i], min1
		} else if nums[i] < min2 {
			min2 = nums[i]
		}
	}

	if max1*max2*max3 > min1*min2*max1 {
		return max1 * max2 * max3
	}
	return min1 * min2 * max1
}
```
