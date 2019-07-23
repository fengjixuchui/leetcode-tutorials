## Question

https://leetcode.com/problems/top-k-frequent-elements/

## Solutions

```go
func topKFrequent(nums []int, k int) []int {
	// key   : number
	// value : frequency
	freq := map[int]int{}
	// index : frequency
	// value : numbers
	bucket := make([][]int, len(nums)+1)
	for i := 0; i < len(bucket); i++ {
		bucket[i] = make([]int, 0)
	}

	for i := 0; i < len(nums); i++ {
		freq[nums[i]]++
	}

	for number, frequency := range freq {
		bucket[frequency] = append(bucket[frequency], number)
	}

	list := make([]int, 0)
	for i := len(bucket) - 1; i > 0; i-- {
		if len(bucket[i]) != 0 {
			list = append(list, bucket[i]...)
		}
	}

	return list[:k]
}
```
