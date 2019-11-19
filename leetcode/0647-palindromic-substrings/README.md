## Question

https://leetcode.com/problems/palindromic-substrings/

## Solutions

```go
// Time: O(n^2), Space: O(n^2)
func countSubstrings(s string) int {
	if len(s) == 0 {
		return 0
	}

	count, n := 0, len(s)
	d := make([][]bool, n)
	for i := 0; i < n; i++ {
		d[i] = make([]bool, n)
	}

	for i := n - 1; i >= 0; i-- {
		for j := i; j < n; j++ {
			if i == j {
				d[i][j] = true
			} else if i+1 == j {
				d[i][j] = s[i] == s[j]
			} else {
				d[i][j] = s[i] == s[j] && d[i+1][j-1]
			}
			if d[i][j] {
				count++
			}
		}
	}

	return count
}
```

## Tutorials

- https://algocasts.io/episodes/dbGY2p5V
