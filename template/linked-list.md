## Linked List

通用模板

```go
func f(head *ListNode) *ListNode {
	dummy := new(ListNode)
	dummy.Next = head
    pre := dummy
    cur := dummy.Next
}
```
