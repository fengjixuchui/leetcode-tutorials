## Question

https://leetcode.com/problems/hamming-distance/

## Solutions

```go
func hammingDistance(x int, y int) int {
	if x == y {
		return 0
	}

	distance := 0
	for i := 0; i < 32; i++ {
		if (x^y)&1 == 1 {
			distance++
		}
		x >>= 1
		y >>= 1
	}

	return distance
}
```
