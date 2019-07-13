## Question

https://leetcode.com/problems/next-permutation/

## Solutions

```go
func nextPermutation(nums []int) {
	if nums == nil || len(nums) < 2 {
		return
	}

	n := len(nums)
	p := n - 2

	for p >= 0 && nums[p] >= nums[p+1] {
		p--
	}

	if p >= 0 {
		i := n - 1
		for i > p && nums[i] <= nums[p] {
			i--
		}
		nums[p], nums[i] = nums[i], nums[p]
	}

	i, j := p+1, n-1
	for i < j {
		nums[i], nums[j] = nums[j], nums[i]
		i++
		j--
	}
}
```
