## Question

https://leetcode.com/problems/remove-duplicates-from-sorted-list/

## Solutions

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func deleteDuplicates(head *ListNode) *ListNode {
    if head == nil {
        return head
    }

    cur, next := head, head.Next
    for next != nil {
        if (cur.Val == next.Val) {
            cur.Next = next.Next
        } else {
            cur = cur.Next
        }
        next = next.Next
    }

    return head
}
```
