## Question

https://leetcode.com/problems/number-of-1-bits/

## Solutions

```go
// Time: O(1), Space: O(1)
func hammingWeight(num uint32) int {
	count := 0

	for num != 0 {
		if num&1 == 1 {
			count++
		}
		num = num >> 1
	}

	return count
}
```
