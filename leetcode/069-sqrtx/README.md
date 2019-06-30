## Question

https://leetcode.com/problems/069-sqrtx/

## Solutions

```go
func mySqrt(x int) int {
    low, high := 0, x

    for low <= high {
        mid := low + (high - low) / 2
        mid2 := mid*mid
        if mid2 == x {
            return mid
        } else if mid2 > x {
            high = mid - 1
        } else {
            low = mid + 1
        }
    }

    return high
}
```
