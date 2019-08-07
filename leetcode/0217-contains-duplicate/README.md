## Question

https://leetcode.com/problems/contains-duplicate/

```go
func containsDuplicate(nums []int) bool {
	hashSet := map[int]bool{}

	for i := 0; i < len(nums); i++ {
		if existed := hashSet[nums[i]]; existed {
			return true
		}
		hashSet[nums[i]] = true
	}

	return false
}
```
