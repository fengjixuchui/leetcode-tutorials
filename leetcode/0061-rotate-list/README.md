## Question

https://leetcode.com/problems/rotate-list/

## Solutions

```go
// Time: O(n), Space: O(1)
func rotateRight(head *ListNode, k int) *ListNode {
	// No need to rotate.
	if head == nil || k == 0 {
		return head
	}

	dummy := new(ListNode)
	dummy.Next = head

	nodeCount := 0
	n := head
	for n != nil {
		nodeCount++
		n = n.Next
	}
	k = k % nodeCount

	// No need to rotate.
	if k == 0 {
		return head
	}

	fast, slow := dummy, dummy
	for ; k > 0; k-- {
		fast = fast.Next
	}

	for fast.Next != nil {
		fast = fast.Next
		slow = slow.Next
	}

	newHead := slow.Next
	slow.Next = nil
	fast.Next = head

	return newHead
}
```
