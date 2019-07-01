## Question

https://leetcode.com/problems/pascals-triangle/

## Solutions

```go
func generate(numRows int) [][]int {
	if numRows < 1 {
		return [][]int{}
	}

	result := make([][]int, numRows)
	result[0] = []int{1}

	for row := 1; row < numRows; row++ {
		result[row] = make([]int, row+1)
		for column := 0; column <= row; column++ {
			if column == 0 || column == row {
				result[row][column] = 1
			} else {
				result[row][column] = result[row-1][column-1] + result[row-1][column]
			}
		}
	}

	return result
}
```
