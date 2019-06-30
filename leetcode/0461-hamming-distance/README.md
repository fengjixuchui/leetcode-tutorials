## Question

https://leetcode.com/problems/hamming-distance/

## Solutions

```go
func numberOfOne(n int) int {
    mask, count := 1, 0

    for mask != 0 {
        if (n & mask) != 0 {
            count++
        }
        mask <<= 1
    }

    return count
}

func hammingDistance(x int, y int) int {
    return numberOfOne(x ^ y)
}
```
