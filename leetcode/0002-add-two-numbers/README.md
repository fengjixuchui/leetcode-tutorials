## Question

https://leetcode.com/problems/add-two-numbers/

## Solutions

```go
// Time: O(m+n), Space: O(m+n)
func addTwoNumbers(l1 *ListNode, l2 *ListNode) *ListNode {
	dummy := ListNode{}
	head := &dummy
	carry := 0

	for l1 != nil || l2 != nil || carry != 0 {
		sum := 0

		if l1 != nil {
			sum += l1.Val
			l1 = l1.Next
		}
		if l2 != nil {
			sum += l2.Val
			l2 = l2.Next
		}

		sum += carry
		carry = sum / 10

		head.Next = &ListNode{Val: sum % 10}
		head = head.Next
	}

	return dummy.Next
}
```
