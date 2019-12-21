## Question

https://leetcode.com/problems/merge-two-sorted-lists/

## Solutions

```go
// Time: O(m+n), Space: O(1)
func mergeTwoLists(l1 *ListNode, l2 *ListNode) *ListNode {
	if l1 != nil && l2 == nil {
		return l1
	}
	if l1 == nil && l2 != nil {
		return l2
	}

	dummy := &ListNode{}
	cur := dummy

	for l1 != nil && l2 != nil {
		if l1.Val > l2.Val {
			cur.Next = l2
			l2 = l2.Next
			cur = cur.Next
		} else {
			cur.Next = l1
			l1 = l1.Next
			cur = cur.Next
		}
	}

	if l1 != nil && l2 == nil {
		cur.Next = l1
	}
	if l1 == nil && l2 != nil {
		cur.Next = l2
	}

	return dummy.Next
}
```
