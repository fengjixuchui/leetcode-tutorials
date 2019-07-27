## Question

https://leetcode.com/problems/reverse-linked-list/

## Solutions

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func reverseList(head *ListNode) *ListNode {
	cur := head
	var pre *ListNode

	for cur != nil {
		cur.Next, cur, pre = pre, cur.Next, cur
	}
	return pre
}
```
