## Question

https://leetcode.com/problems/container-with-most-water/

## Solutions

```go
func maxArea(height []int) int {
    max := 0

    i, j := 0, len(height)

    for i < j {
        cur := max(height[i], height[j]) * (j - i)
        max = Max(max, cur)
        if height[i] < height[j] {
            j--
        } else {
            i++
        }
    }
}

func Max (a, b int) int {
    if a > b {
        return a
    }
    return b
}
```
