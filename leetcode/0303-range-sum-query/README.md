## Solutions

```go
type NumArray struct {
	accu []int
}

func Constructor(nums []int) NumArray {
	accu := make([]int, 1)
	for _, v := range nums {
		accu = append(accu, accu[len(accu)-1]+v)
	}
	return NumArray{
		accu: accu,
	}
}

func (this *NumArray) SumRange(i int, j int) int {
	return this.accu[j+1] - this.accu[i]
}


/**
 * Your NumArray object will be instantiated and called as such:
 * obj := Constructor(nums);
 * param_1 := obj.SumRange(i,j);
 */
```
