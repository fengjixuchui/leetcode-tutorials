## Question

https://leetcode.com/problems/swap-nodes-in-pairs/

## Solutions

```go
func swapPairs(head *ListNode) *ListNode {
	if head == nil {
		return head
	}

	dummy := &ListNode{}
	dummy.Next = head
	pre := dummy
	cur := dummy.Next

	for pre.Next != nil && pre.Next.Next != nil {
		pre.Next = cur.Next
		cur.Next = cur.Next.Next
		pre.Next.Next = cur
		pre = cur
		cur = cur.Next
	}

	return dummy.Next
}
```
