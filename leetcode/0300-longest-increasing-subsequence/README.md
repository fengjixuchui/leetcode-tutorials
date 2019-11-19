## Question

https://leetcode.com/problems/longest-increasing-subsequence/

## Solutions

```go
// Time: O(n^2), Space: O(1)
func lengthOfLIS(nums []int) int {
	if nums == nil || len(nums) == 0 {
		return 0
	}

	n, maxLen := len(nums), 1
	d := make([]int, n)
	d[0] = 1

	for i := 1; i < n; i++ {
		len := 1
		for j := 0; j < i; j++ {
			if nums[i] > nums[j] {
				len = max(len, d[j]+1)
			}
		}
		d[i] = len
		maxLen = max(maxLen, d[i])
	}

	return maxLen
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```

## Tutorials

- https://www.youtube.com/watch?v=fV-TF4OvZpk
