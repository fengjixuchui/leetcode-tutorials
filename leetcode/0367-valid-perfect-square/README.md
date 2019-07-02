## Question

https://leetcode.com/problems/valid-perfect-square/

## Solutions

```go
func isPerfectSquare(num int) bool {
    if num == 1 {
        return true
    }

    low, high := 0, num

    for low <= high {
        mid := low + (high - low) / 2
        if mid * mid == num {
            return true
        } else if mid * mid > num {
            high--
        } else {
            low++
        }
    }

    return false
}
```
