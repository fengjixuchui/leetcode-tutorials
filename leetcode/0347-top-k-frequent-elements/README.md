## Question

https://leetcode.com/problems/top-k-frequent-elements/

## Solutions

```go
// Time: O(n), Space: O(n)
func topKFrequent(nums []int, k int) []int {
	// num, freq
	freq := make(map[int]int)
	// freq, nums
	bucket := make(map[int][]int)
	for i := 0; i < len(nums)+1; i++ {
		bucket[i] = make([]int, 0)
	}

	for _, num := range nums {
		freq[num]++
	}
	for num, freq := range freq {
		bucket[freq] = append(bucket[freq], num)
	}

	list := []int{}
	for i := len(bucket); i > 0; i-- {
		if len(bucket[i]) != 0 {
			list = append(list, bucket[i]...)
		}
	}

	return list[:k]
}
```
