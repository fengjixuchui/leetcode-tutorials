## Question

https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/

## Solutions

```go
func deleteDuplicates(head *ListNode) *ListNode {
	dummy := new(ListNode)
	dummy.Next = head

	prev, cur := dummy, dummy.Next

	for cur != nil {
		for cur.Next != nil && (cur.Val == cur.Next.Val) {
			cur = cur.Next
		}
		if prev.Next != cur {
			prev.Next = cur.Next
		} else {
			prev = prev.Next
		}
		cur = prev.Next
	}

	return dummy.Next
}
```
