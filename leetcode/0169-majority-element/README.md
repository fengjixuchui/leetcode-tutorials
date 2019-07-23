## Question

https://leetcode.com/problems/169-majority-element/

## Solutions

```go
func majorityElement(nums []int) int {
	freq := make(map[int]int)

	for i := 0; i < len(nums); i++ {
		freq[nums[i]]++
		if freq[nums[i]] > len(nums)/2 {
			return nums[i]
		}
	}

	return -1
}
```
