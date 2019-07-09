## Question

https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/

## Solutions

```go
func findDisappearedNumbers(nums []int) []int {
	for i := 0; i < len(nums); i++ {
		idx := abs(nums[i]) - 1
		if nums[idx] > 0 {
			nums[idx] = -nums[idx]
		}
	}

	result := make([]int, 0, len(nums))
	for i := 0; i < len(nums); i++ {
		if nums[i] > 0 {
			result = append(result, i+1)
		}
	}

	return result
}

func abs(a int) int {
	if a < 0 {
		return -a
	}
	return a
}
```
