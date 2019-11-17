## Question

https://leetcode.com/problems/find-all-duplicates-in-an-array/

## Solutions

```go
// Time: O(n), Space: O(n)
func findDuplicates(nums []int) []int {
	res := []int{}

	if len(nums) == 0 {
		return res
	}

	visited := map[int]bool{}

	for _, num := range nums {
		if visited[num] {
			res = append(res, num)
		}
		visited[num] = true
	}

	return res
}
```

```go
// Time: O(n), Space: O(1)
func findDuplicates(nums []int) []int {
	res := []int{}

	if len(nums) == 0 {
		return res
	}

	for _, num := range nums {
    num = abs(num)
		idx := num - 1
		if nums[idx] < 0 {
			res = append(res, num)
		} else {
			nums[idx] = -nums[idx]
		}
	}

	return res
}

func abs(n int) int {
	if n < 0 {
		return -n
	}
	return n
}
```
