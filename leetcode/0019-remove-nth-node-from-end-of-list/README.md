## Question

https://leetcode.com/problems/remove-nth-node-from-end-of-list/

## Solutions

```go
// O(n) time | O(1) space
func removeNthFromEnd(head *ListNode, n int) *ListNode {
	dummy := &ListNode{}
	dummy.Next = head

	// slow, fast := head, head will cause error.
	slow, fast := dummy, dummy

	for i := 0; i < n; i++ {
		fast = fast.Next
	}

	for fast.Next != nil {
		slow = slow.Next
		fast = fast.Next
	}

	slow.Next = slow.Next.Next

	return dummy.Next
}
```
