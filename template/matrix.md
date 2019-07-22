## Matrix

```go
func copy(nums [][]int) [][]int {
	if nums == nil || len(nums) == 0 {
		return nums
	}

	// get the row count and column count
	r, c := len(nums), len(nums[0])
	// get the number count
	count := r * c

	// create new matirx
	result := make([][]int, nr)
	for i := 0; i < nr; i++ {
		result[i] = make([]int, nc)
	}

    row := i / nc
    col := i % nc
    result[row][col] = nums[row][col]

	return result
}
```
