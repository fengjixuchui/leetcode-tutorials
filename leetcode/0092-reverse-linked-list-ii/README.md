## Question

https://leetcode.com/problems/reverse-linked-list-ii/

## Solutions

```go
func reverseBetween(head *ListNode, m int, n int) *ListNode {
	dummy := new(ListNode)
	dummy.Next = head

	left := dummy
	for i := 1; i < m; i++ {
		left = left.Next
	}

	middle := left.Next
	right := middle.Next

	for i := 0; i < n-m; i++ {
		// l    m    r
		// 1 -> 2 -> 3 -> 4 -> 5
		// l         m    r
		// 1 -> 3 -> 2 -> 4 -> 5
		middle.Next = right.Next
		right.Next = left.Next
		left.Next = right
		right = middle.Next
	}

	return dummy.Next
}
```
