## Question

https://leetcode.com/problems/sqrtx/

## Solutions

```go
// Time: O(logn), Space: O(1)
func mySqrt(x int) int {
	left, right := 0, x

	for left+1 < right {
		middle := left + (right-left)/2
		square := middle * middle

		if square == x {
			return middle
		} else if square > x {
			right = middle
		} else {
			left = middle
		}
	}

	if right*right == x {
		return right
	} else if left*left == x {
		return left
	} else {
		return left
	}
}
```
