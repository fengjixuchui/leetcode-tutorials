## Question

https://leetcode.com/problems/linked-list-cycle/

## Solutions

```go
// O(n)
func hasCycle(head *ListNode) bool {
	// Handle edge cases.
	if head == nil {
		return false
	}

	slow, fast := head, head.Next

	for fast != nil && fast.Next != nil {
		if slow == fast {
			return true
		}
		slow = slow.Next
		fast = fast.Next.Next
	}

	return false
}
```
