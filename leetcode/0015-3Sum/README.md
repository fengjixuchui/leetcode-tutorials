## Question

https://leetcode.com/problems/3sum/

## Solutions

```go
// O(n^2) time | O(1) space
func threeSum(nums []int) [][]int {
	sort.Ints(nums)

	result := [][]int{}

	for i := 0; i <= len(nums)-3; i++ {
		if i == 0 || nums[i] != nums[i-1] {
			left := i + 1
			right := len(nums) - 1

			for left < right {
				if nums[i]+nums[left]+nums[right] == 0 {
					result = append(result, []int{nums[i], nums[left], nums[right]})
				}

				if nums[i]+nums[left]+nums[right] < 0 {
					currentLeft := left
					for nums[left] == nums[currentLeft] && left < right {
						left++
					}
				} else {
					currentRight := right
					for nums[right] == nums[currentRight] && left < right {
						right--
					}
				}
			}
		}
	}

	return result
}
```
