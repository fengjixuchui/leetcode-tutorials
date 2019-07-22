## Question

https://leetcode.com/problems/reshape-the-matrix/

## Solutions

```go
func matrixReshape(nums [][]int, nr int, nc int) [][]int {
	if nums == nil || len(nums) == 0 {
		return nums
	}

	// get the row count and column count
	r, c := len(nums), len(nums[0])
	// get the number count
	count := r * c

	// return the origin if the total number is not match
	if count != nr*nc {
		return nums
	}

	// create new matirx
	result := make([][]int, nr)
	for i := 0; i < nr; i++ {
		result[i] = make([]int, nc)
	}

	for i := 0; i < count; i++ {
		oldRow := i / c
		oldCol := i % c
		newRow := i / nc
		newCol := i % nc
		result[newRow][newCol] = nums[oldRow][oldCol]
	}

	return result
}
```
