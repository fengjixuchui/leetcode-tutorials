## Question

https://leetcode.com/problems/sliding-window-maximum/

## Solutions

```go
// Time: O(n), Space: O(k)
func maxSlidingWindow(nums []int, k int) []int {
	res := []int{}

	if len(nums) == 0 {
		return res
	}
	if k > len(nums) {
		return res
	}

	queue := []int{}

	for i := 0; i < k; i++ {
		for len(queue) != 0 && nums[i] >= nums[queue[len(queue)-1]] {
			queue = queue[:len(queue)-1]
		}
		queue = append(queue, i)
	}
	res = append(res, nums[queue[0]])

	for i := k; i < len(nums); i++ {
		for len(queue) != 0 && nums[i] >= nums[queue[len(queue)-1]] {
			queue = queue[:len(queue)-1]
		}
		for len(queue) != 0 && queue[0] <= i-k {
			queue = queue[1:]
		}
		queue = append(queue, i)
		res = append(res, nums[queue[0]])
	}

	return res
}
```
