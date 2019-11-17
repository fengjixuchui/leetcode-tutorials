## Question

https://leetcode.com/problems/3sum/

## Solutions

```go
// O(n^2) time | O(1) space
func threeSum(nums []int) [][]int {
	res := [][]int{}

	if nums == nil || len(nums) == 0 {
		return res
	}

	sort.Ints(nums)

	for i := 0; i < len(nums); i++ {
		l := i + 1
		r := len(nums) - 1

		// remove duplicates
		if i != 0 && nums[i-1] == nums[i] {
			continue
		}

		for l < r {
			sum := nums[i] + nums[l] + nums[r]
			if sum > 0 {
				r--
			} else if sum < 0 {
				l++
			} else {
				// sum == 0
				res = append(res, []int{nums[i], nums[l], nums[r]})
				r--
				l++
				// remove duplicates
				for l < r && nums[r+1] == nums[r] {
					r--
				}
				for l < r && nums[l-1] == nums[l] {
					l++
				}
			}
		}
	}

	return res
}
```

## Tutorials

- https://www.youtube.com/watch?v=y-zBV7uUkyI
