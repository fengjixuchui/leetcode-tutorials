## Question

https://leetcode.com/problems/shuffle-an-array/

## Solutions

```go
type Solution struct {
	nums []int
}

func Constructor(nums []int) Solution {
	return Solution{
		nums: nums,
	}
}

/** Resets the array to its original configuration and return it. */
func (this Solution) Reset() []int {
	return this.nums
}

/** Returns a random shuffling of the array. */
func (this Solution) Shuffle() []int {
	result := make([]int, len(this.nums))
	copy(result, this.nums)

	for i := len(result) - 1; i > 0; i-- {
		j := rand.Intn(i + 1)
		result[i], result[j] = result[j], result[i]
	}
	return result
}
```
