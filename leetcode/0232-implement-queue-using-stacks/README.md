## Question

https://leetcode.com/problems/implement-queue-using-stacks/

## Solutions

```go
type MyQueue struct {
	stack1 []int // push new element
	stack2 []int // pop out the first elelmet
}

/** Initialize your data structure here. */
func Constructor() MyQueue {
	return MyQueue{
		stack1: make([]int, 0),
		stack2: make([]int, 0),
	}
}

/** Push element x to the back of queue. */
func (this *MyQueue) Push(x int) {
	this.stack1 = append(this.stack1, x)
}

/** Removes the element from in front of queue and returns that element. */
func (this *MyQueue) Pop() int {
	if len(this.stack2) == 0 {
		for i := len(this.stack1) - 1; i >= 0; i-- {
			this.stack2 = append(this.stack2, this.stack1[i])
		}
		this.stack1 = []int{}
	}
	firstElem := this.stack2[len(this.stack2)-1]
	this.stack2 = this.stack2[:len(this.stack2)-1]
	return firstElem
}

/** Get the front element. */
func (this *MyQueue) Peek() int {
	if len(this.stack2) == 0 {
		for i := len(this.stack1) - 1; i >= 0; i-- {
			this.stack2 = append(this.stack2, this.stack1[i])
		}
		this.stack1 = []int{}
	}
	firstElem := this.stack2[len(this.stack2)-1]
	return firstElem
}

/** Returns whether the queue is empty. */
func (this *MyQueue) Empty() bool {
	return len(this.stack1) == 0 && len(this.stack2) == 0
}
```
