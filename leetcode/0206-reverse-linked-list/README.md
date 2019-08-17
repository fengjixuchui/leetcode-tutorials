## Question

https://leetcode.com/problems/reverse-linked-list/

## Solutions

```go
func reverseList(head *ListNode) *ListNode {
	if head == nil {
		return head
	}

	dummy := &ListNode{}
	dummy.Next = head
	var pre *ListNode
	cur := dummy.Next

	for cur != nil {
		next := cur.Next
		cur.Next = pre
		pre = cur
		cur = next
	}

	return pre
}
```
