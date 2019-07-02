## Question

https://leetcode.com/problems/remove-nth-node-from-end-of-list/

## Solutions

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func removeNthFromEnd(head *ListNode, n int) *ListNode {
    dummy := &ListNode{}
    dummy.Next = head
    p, q := dummy, dummy

    for ; n > 0 && q.Next != nil; n-- {
        q = q.Next
    }
    // n != 0 means n is bigger than the list length.
    if n != 0 {
        return dummy.Next
    }

    for q.Next != nil {
        p = p.Next
        q = q.Next
    }

    p.Next = p.Next.Next

    return dummy.Next
}
```
