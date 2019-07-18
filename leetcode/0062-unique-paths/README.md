## Question

https://leetcode.com/problems/unique-paths/

## Solutions

```go
// We use m = 7 and n = 3 as example.
// m -> row count
// n -> column count
func uniquePaths(m int, n int) int {
	// d stores how many ways can reach the location.
	d := make([][]int, m)
	for i := 0; i < m; i++ {
		d[i] = make([]int, n)
	}

	// Initial location set to 1.
	d[0][0] = 1

	// Here's what d looks for now
	// [1 0 0 0 0 0 0]
	// [0 0 0 0 0 0 0]
	// [0 0 0 0 0 0 0]

	// When row = 0, there's only one way to go to the location (left->right).
	for col := 0; col < n; col++ {
		d[0][col] = 1
	}

	// Here's what d looks for now
	// [1 1 1 1 1 1 1]
	// [0 0 0 0 0 0 0]
	// [0 0 0 0 0 0 0]

	// When col = 0, there's only one way to go to the location (top->down).
	for row := 0; row < m; row++ {
		d[row][0] = 1
	}

	// Here's what d looks for now
	// [1 1 1 1 1 1 1]
	// [1 0 0 0 0 0 0]
	// [1 0 0 0 0 0 0]

	// For the other location, we can go from left or top.
	for row := 1; row < m; row++ {
		for col := 1; col < n; col++ {
			d[row][col] = d[row-1][col] + d[row][col-1]
		}
	}

	// Here's what d looks for now
	// [1 1 1  1  1  1  1]
	// [1 2 3  4  5  6  7]
	// [1 3 6 10 15 21 28]

	// Return the bottom right value.
	return d[m-1][n-1]
}
```
