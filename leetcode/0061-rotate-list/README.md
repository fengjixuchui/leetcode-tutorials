## Question

https://leetcode.com/problems/rotate-list/

## Solutions

```go
func rotateRight(head *ListNode, k int) *ListNode {
	if head == nil || head.Next == nil || k == 0 {
		return head
	}

	n := 1
	end := head
	for end.Next != nil {
		end = end.Next
		n++
	}
	end.Next = head

	k %= n

	newEnd := head
	for i := 0; i < n-k-1; i++ {
		newEnd = newEnd.Next
	}

	newHead := newEnd.Next
	newEnd.Next = nil

	return newHead
}
```
