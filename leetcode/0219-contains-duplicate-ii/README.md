## Question

https://leetcode.com/problems/contains-duplicate-ii/

```go
func containsNearbyDuplicate(nums []int, k int) bool {
	hashMap := make(map[int]int)

	for currentIndex, v := range nums {
		index, ok := hashMap[v]
		if ok {
			if (currentIndex - index) <= k {
				return true
			}
		}
		hashMap[v] = currentIndex
	}

	return false
}
```
