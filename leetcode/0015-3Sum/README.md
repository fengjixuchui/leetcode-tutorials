## Question

https://leetcode.com/problems/3sum/

## Solutions

```go
// Example:
// Input: [-1,0,2,1,2,-1,-4,-1]
// Sorted: [-4,-1,-1,-1,0,1,2,2]

func threeSum(nums []int) [][]int {
    sort.Ints(nums)

    result := [][]int{}

    for i := 0; i < len(nums)-1; i++ {
      // remove duplicates
        if i > 0 && nums[i] == nums[i-1] {
            continue
        }
        j := i + 1
        k := len(nums) - 1
        for j < k {
            b := nums[j]
            c := nums[k]
            if nums[i]+b+c > 0 {
                k--
            } else if nums[i]+b+c < 0 {
                j++
            } else {
                result = append(result, []int{nums[i], b, c})
                // remove duplicates
                for j < k && nums[j] == nums[j+1] {
                    j++
                }
                // remove duplicates
                for j < k && nums[k] == nums[k-1] {
                    k--
                }
                j++
                k--
            }
        }
    }
    return result
}
```
