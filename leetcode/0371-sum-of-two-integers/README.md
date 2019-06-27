## Question

https://leetcode.com/problems/0371-sum-of-two-integers/

## Solutions

```go
func getSum(a int, b int) int {
    for b != 0 {
        sum := a ^ b
        carry := (a & b) << 1
        a = sum
        b = carry
    }
    return a
}
```
