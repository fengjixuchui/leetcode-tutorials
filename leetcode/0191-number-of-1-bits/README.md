## Question

https://leetcode.com/problems/number-of-1-bits/

## Solutions

```go
func hammingWeight(num uint32) int {
	mask, count := uint32(1), 0

	for mask != 0 {
		if (num & mask) != 0 {
			count++
		}
		mask <<= 1
	}

	return count
}
```
