## Question

https://leetcode.com/problems/intersection-of-two-arrays/

## Solutions

```go
func intersection(nums1 []int, nums2 []int) []int {
	if len(nums1) == 0 && len(nums2) == 0 {
		return []int{}
	}

	hashSet1 := map[int]bool{}
	hashSet2 := map[int]bool{}

	for i := 0; i < len(nums1); i++ {
		if existed := hashSet1[nums1[i]]; !existed {
			hashSet1[nums1[i]] = true
		}
	}
	for i := 0; i < len(nums2); i++ {
		if existed := hashSet2[nums2[i]]; !existed {
			hashSet2[nums2[i]] = true
		}
	}

	res := []int{}
	for num := range hashSet2 {
		if existed := hashSet1[num]; existed {
			res = append(res, num)
		}
	}

	return res
}
```
