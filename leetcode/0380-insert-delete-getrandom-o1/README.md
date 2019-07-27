## Question

https://leetcode.com/problems/insert-delete-getrandom-o1/

## Solutions

```go
import (
	"math/rand"
)

type RandomizedSet struct {
	// key   : number
	// value : index in value slice
	hashTable map[int]int
	nums      []int
}

/** Initialize your data structure here. */
func Constructor() RandomizedSet {
	return RandomizedSet{
		hashTable: map[int]int{},
		nums:      make([]int, 0),
	}
}

/** Inserts a value to the set. Returns true if the set did not already contain the specified element. */
func (this *RandomizedSet) Insert(val int) bool {
	if _, existed := this.hashTable[val]; existed {
		return false
	}
	this.nums = append(this.nums, val)
	this.hashTable[val] = len(this.nums) - 1
	return true
}

/** Removes a value from the set. Returns true if the set contained the specified element. */
func (this *RandomizedSet) Remove(val int) bool {
	if _, existed := this.hashTable[val]; !existed {
		return false
	}
	curIdx := this.hashTable[val]
	lastIdx := len(this.nums) - 1
	lastNumber := this.nums[lastIdx]
	this.hashTable[lastNumber] = curIdx
	delete(this.hashTable, val)
	// Put lastNumber into current index.
	this.nums[curIdx] = lastNumber
	// Remove the last number from slice
	this.nums = this.nums[:len(this.nums)-1]
	return true
}

/** Get a random element from the set. */
func (this *RandomizedSet) GetRandom() int {
	return this.nums[rand.Int()%len(this.nums)]
}
```
