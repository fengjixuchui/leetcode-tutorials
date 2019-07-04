## Question

https://leetcode.com/problems/implement-queue-using-stacks/

## Solutions

```go
type MyQueue struct {
	in  []int
	out []int
}

/** Initialize your data structure here. */
func Constructor() MyQueue {
	return MyQueue{}
}

/** Push element x to the back of queue. */
func (this *MyQueue) Push(x int) {
	this.in = append(this.in, x)
}

/** Removes the element from in front of queue and returns that element. */
func (this *MyQueue) Pop() int {
	if len(this.out) == 0 {
		for _, num := range this.in {
			this.out = append(this.out, num)
		}
		this.in = make([]int, 0)
	}
	first := this.out[0]
	this.out = this.out[1:]
	return first
}

/** Get the front element. */
func (this *MyQueue) Peek() int {
	if len(this.out) == 0 {
		for _, num := range this.in {
			this.out = append(this.out, num)
		}
		this.in = make([]int, 0)
	}
	if len(this.out) == 0 {
		return 0
	}
	return this.out[0]
}

/** Returns whether the queue is empty. */
func (this *MyQueue) Empty() bool {
	return len(this.out) == 0 && len(this.in) == 0
}
```
