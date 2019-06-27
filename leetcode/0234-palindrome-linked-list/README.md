## Question

https://leetcode.com/problems/0234-palindrome-linked-list/

## Solutions

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func isPalindrome(head *ListNode) bool {
	stack := []int{}

	p := head
	for p != nil {
		stack = append(stack, p.Val)
		p = p.Next
	}

	for head != nil && len(stack) != 0 {
		curr := stack[len(stack)-1]
		stack = stack[:len(stack)-1]
		if head.Val != curr {
			return false
		}
        head = head.Next
	}

	return true
}
```
