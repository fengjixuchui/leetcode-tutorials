## Question

https://leetcode.com/problems/set-matrix-zeroes/

## Solutions

```go
// Time: O(m*n), Space: O(1)
func setZeroes(matrix [][]int) {
	if matrix == nil || len(matrix) == 0 || len(matrix[0]) == 0 {
		return
	}

	m, n := len(matrix), len(matrix[0])

	firstRowZero, firstColZero := false, false

	for row := 0; row < m; row++ {
		if matrix[row][0] == 0 {
			firstColZero = true
			break
		}
	}
	for col := 0; col < n; col++ {
		if matrix[0][col] == 0 {
			firstRowZero = true
			break
		}
	}

	for row := 1; row < m; row++ {
		for col := 1; col < n; col++ {
			if matrix[row][col] == 0 {
				matrix[0][col] = 0
				matrix[row][0] = 0
			}
		}
	}

	for row := 1; row < m; row++ {
		for col := 1; col < n; col++ {
			if matrix[0][col] == 0 || matrix[row][0] == 0 {
				matrix[row][col] = 0
			}
		}
	}

	if firstRowZero {
		for col := 0; col < n; col++ {
			matrix[0][col] = 0
		}
	}
	if firstColZero {
		for row := 0; row < m; row++ {
			matrix[row][0] = 0
		}
	}
}
```

```go
// Time: O(m*n), Space: O(m+n)
func setZeroes(matrix [][]int)  {
    m, n := len(matrix), len(matrix[0])

    rows := make([]bool, m)
    cols := make([]bool, n)

    for i := 0; i < m; i++ {
        for j := 0; j < n; j++ {
            if matrix[i][j] == 0 {
                rows[i] = true
                cols[j] = true
            }
        }
    }

    for i := 0; i < m; i++ {
        for j := 0; j < n; j++ {
            if rows[i] || cols[j] {
                matrix[i][j] = 0
            }
        }
    }
}
```

## Tutorials

- https://www.youtube.com/watch?v=1KnLIAvTxjQ
