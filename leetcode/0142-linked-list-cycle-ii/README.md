## Question

https://leetcode.com/problems/linked-list-cycle-ii/

## Solutions

```go
func detectCycle(head *ListNode) *ListNode {
	fast, slow := head, head

	for fast != nil && fast.Next != nil {
		fast = fast.Next.Next
		slow = slow.Next

		if fast == slow {
			p := head
			for p != slow {
				p = p.Next
				slow = slow.Next
			}
			return slow
		}
	}

	return nil
}
```
