## Question

https://leetcode.com/problems/insertion-sort-list/

## Solutions

```go
func sortedInset(head *ListNode, node *ListNode) *ListNode {
	if node == nil {
		return head
	}

	if head == nil || node.Val <= head.Val {
		node.Next = head
		return node
	}

	cur := head
	for cur.Next != nil && cur.Next.Val < node.Val {
		cur = cur.Next
	}

	node.Next = cur.Next
	cur.Next = node

	return head
}

// T: O(n^2), S: O(n)
func insertionSortList(head *ListNode) *ListNode {
	if head == nil {
		return head
	}

	cur := head
	var sorted *ListNode

	for cur != nil {
        temp := cur.Next
		sorted = sortedInset(sorted, cur)
		cur = temp
	}

	return sorted
}
```
