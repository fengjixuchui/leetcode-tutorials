## Solutions

```go
func intersection(nums1 []int, nums2 []int) []int {
	hashMap := make(map[int]bool)

	for _, n := range nums1 {
		if _, ok := hashMap[n]; !ok {
			hashMap[n] = true
		}
	}

	res := make([]int, 0)

	for _, n := range nums2 {
		if _, ok := hashMap[n]; ok {
			res = append(res, n)
			delete(hashMap, n)
		}
	}

	return res
}
```
