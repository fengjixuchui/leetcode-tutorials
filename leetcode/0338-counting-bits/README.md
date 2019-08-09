## Question

https://leetcode.com/problems/counting-bits/

## Solutions

```go
func countBits(num int) []int {
	counts := []int{0}

	for i := 1; i <= num; i++ {
		count := counts[(i>>1)] + (i & 1)
		counts = append(counts, count)
	}

	return counts
}
```
