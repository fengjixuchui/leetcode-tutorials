## Question

https://leetcode.com/problems/partition-list/

## Solutions

```go
func partition(head *ListNode, x int) *ListNode {
	if head == nil {
		return head
	}

	smaller, greater := new(ListNode), new(ListNode)
	ps, pg, p := smaller, greater, head

	for p != nil {
		if p.Val < x {
			ps.Next = p
			ps = ps.Next
		} else {
			pg.Next = p
			pg = pg.Next
		}
		p = p.Next
	}
	ps.Next = greater.Next
	pg.Next = nil

	return smaller.Next
}
```
