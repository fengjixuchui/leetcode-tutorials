## Linked List

```go
func f(head *ListNode) *ListNode {
	dummy := &ListNode{}
	dummy.Next = head
    pre := dummy // or var pre *ListNode
    cur := dummy.Next
}
```
