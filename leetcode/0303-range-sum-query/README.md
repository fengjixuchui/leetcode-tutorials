## Question

https://leetcode.com/problems/intersection-of-two-arrays/

## Solutions

```go
// input: [-2, 0, 3, -5, 2, -1]
//     d: [0, -2, -2, 1, -4, -2, -3]
//
// The meaning of d:
// add to index: null, 0, 01, 012, 0123, 01234, 012345
//            d: [0,  -2, -2,  1,   -4,   -2,     -3]
type NumArray struct {
	d []int
}

func Constructor(nums []int) NumArray {
	d := make([]int, len(nums)+1)
	d[0] = 0
	for i := 0; i < len(nums); i++ {
		d[i+1] += d[i] + nums[i]
	}
	return NumArray{
		d: d,
	}
}

func (this NumArray) SumRange(i int, j int) int {
	return this.d[j+1] - this.d[i]
}
/**
 * Your NumArray object will be instantiated and called as such:
 * obj := Constructor(nums);
 * param_1 := obj.SumRange(i,j);
 */
```
