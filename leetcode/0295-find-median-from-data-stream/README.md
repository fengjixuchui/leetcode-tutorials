## Question

https://leetcode.com/problems/find-median-from-data-stream/

## Solutions

```go
// O(logn) time | O(1) space
type MedianFinder struct {
	maxHeap *maxHeap
	minHeap *minHeap
}

func Constructor() MedianFinder {
	max, min := &maxHeap{}, &minHeap{}
	heap.Init(max)
	heap.Init(min)
	return MedianFinder{
		maxHeap: max,
		minHeap: min,
	}
}

func (this *MedianFinder) AddNum(num int) {
	if this.maxHeap.Len() == 0 || num < (*this.maxHeap)[0] {
		heap.Push(this.maxHeap, num)
	} else {
		heap.Push(this.minHeap, num)
	}
	// only allow this.maxHeap.Len() == this.minHeap.Len()
	// or         this.maxHeap.Len() == this.minHeap.Len() + 1
	if this.maxHeap.Len() == this.minHeap.Len()+2 {
		heap.Push(this.minHeap, heap.Pop(this.maxHeap))
	}
	if this.minHeap.Len() == this.maxHeap.Len()+1 {
		heap.Push(this.maxHeap, heap.Pop(this.minHeap))
	}
}

func (this *MedianFinder) FindMedian() float64 {
	if this.maxHeap.Len() == this.minHeap.Len() {
		return float64((*this.maxHeap)[0]+(*this.minHeap)[0]) / 2.0
	}
	return float64((*this.maxHeap)[0])
}

type maxHeap []int

func (h *maxHeap) Less(i, j int) bool {
	return (*h)[i] > (*h)[j]
}

func (h *maxHeap) Swap(i, j int) {
	(*h)[i], (*h)[j] = (*h)[j], (*h)[i]
}

func (h *maxHeap) Len() int {
	return len(*h)
}

func (h *maxHeap) Push(v interface{}) {
	*h = append(*h, v.(int))
}

func (h *maxHeap) Pop() interface{} {
	length := len(*h)
	v := (*h)[length-1]
	*h = (*h)[:length-1]
	return v
}

type minHeap []int

func (h *minHeap) Less(i, j int) bool {
	return (*h)[i] < (*h)[j]
}

func (h *minHeap) Swap(i, j int) {
	(*h)[i], (*h)[j] = (*h)[j], (*h)[i]
}

func (h *minHeap) Len() int {
	return len(*h)
}

func (h *minHeap) Push(v interface{}) {
	*h = append(*h, v.(int))
}

func (h *minHeap) Pop() interface{} {
	length := len(*h)
	v := (*h)[length-1]
	*h = (*h)[:length-1]
	return v
}
```

## Tutorials

- https://www.youtube.com/watch?v=cqhED6Xgy9Y
