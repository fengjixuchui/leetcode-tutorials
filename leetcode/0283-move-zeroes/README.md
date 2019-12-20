## Question

https://leetcode.com/problems/move-zeroes/

## Solutions

```go
// Time: O(n), Space: O(1)
func moveZeroes(nums []int) {
	r, w := 0, 0
	for r < len(nums) {
		if nums[r] != 0 {
			nums[r], nums[w] = nums[w], nums[r]
			w++
		}
		r++
	}
}
```
