## Question

https://leetcode.com/problems/longest-consecutive-sequence/

## Solutions

```go
// O(n) time | O(n) space
func longestConsecutive(nums []int) int {
	set := make(map[int]bool)

	for _, num := range nums {
		set[num] = true
	}

	maxLen := 0

	for low := range set {
		if !set[low-1] {
			high := low + 1
			for set[high] {
				high++
			}
			maxLen = Max(maxLen, high-low)
		}
	}

	return maxLen
}

func Max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```

## Tutorials

- https://www.youtube.com/watch?v=02aLxHJDgsA
