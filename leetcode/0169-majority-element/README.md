## Question

https://leetcode.com/problems/169-majority-element/

## Solutions

```go
func majorityElement(nums []int) int {
	if len(nums) == 1 {
		return nums[0]
	}

	hashMap := make(map[int]int)
	half := len(nums) / 2

	for _, v := range nums {
		count, ok := hashMap[v]
		if ok {
			count++
			hashMap[v] = count
			if count > half {
				return v
			}
		} else {
			hashMap[v] = 1
		}
	}

	return 0
}
```
