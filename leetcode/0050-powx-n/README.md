## Question

https://leetcode.com/problems/0050-powx-n/

## Solutions

```go
// In the dividing step, we keep dividing n by 2 recursively until we reach the base case i.e. n == 1
// In the combining step, we get the result, 'r', of the sub-problem and compute the result of the current problem using the two rules below:
// if n is even, the result is r * r (where r is the result of sub-problem)
// if n is odd, the result is x * r * r (where r is the result of sub-problem)

// Time: O(logn), Space: O(logn)
func myPow(x float64, n int) float64 {
	if n == 0 {
		return 1
	}
	if n == 1 {
		return n
	}

	if n < 0 {
		return 1 / myPow(x, -n)
	}

	if n%2 == 0 {
		return myPow(x*x, n/2)
	}
	return x * myPow(x*x, n/2)
}
```
