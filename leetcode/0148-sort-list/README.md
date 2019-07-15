## Question

https://leetcode.com/problems/sort-list/

## Solutions

```go
func quickSort(head, end *ListNode) {
	if head == end || head.Next == end {
		return
	}

	pivot := head.Val
	slow, fast := head, head.Next

	for fast != end {
		if pivot >= fast.Val {
			slow = slow.Next
			slow.Val, fast.Val = fast.Val, slow.Val
		}
		fast = fast.Next
	}
	slow.Val, head.Val = head.Val, slow.Val
	quickSort(head, slow)
	quickSort(slow.Next, end)
}

func sortList(head *ListNode) *ListNode {
	quickSort(head, nil)
	return head
}
```
