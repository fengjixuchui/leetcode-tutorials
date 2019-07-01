## Question

https://leetcode.com/problems/intersection-of-two-arrays-ii/

## Solutions

```go
func intersect(nums1 []int, nums2 []int) []int {
    lookup := make(map[int]int)

    for _, v := range nums1 {
        lookup[v]++
    }

    result := make([]int, 0)
    for _, v := range nums2 {
        if count, ok := lookup[v]; ok {
            if count > 0 {
                result = append(result, v)
                lookup[v] = count - 1
            }
        }
    }

    return result
}
```
