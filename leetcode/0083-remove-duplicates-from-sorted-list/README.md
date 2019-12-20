## Question

https://leetcode.com/problems/remove-duplicates-from-sorted-list/

## Solutions

```go
// Time: O(n), Space: O(1)
func deleteDuplicates(head *ListNode) *ListNode {
	dummy := new(ListNode)
	dummy.Next = head
	pre, cur := dummy, dummy.Next

	for cur != nil {
		for cur.Next != nil && cur.Val == cur.Next.Val {
			cur = cur.Next
		}
		pre.Next = cur
		cur = cur.Next
		pre = pre.Next
	}

	return dummy.Next
}
```
