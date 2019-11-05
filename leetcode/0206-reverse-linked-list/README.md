## Question

https://leetcode.com/problems/reverse-linked-list/

## Solutions

```go
func reverseList(head *ListNode) *ListNode {
	if head == nil {
		return head
	}

	var pre *ListNode
	cur := head

	for cur != nil {
		temp := cur.Next
		cur.Next = pre
		pre = cur
		cur = temp
	}

	return pre
}

// Beginning:
// nil 1->2->3->4->5->NULL
//  p  c  t

// First:
// nil<-1 2->3->4->5->NULL
//      p c

// Second:
// nil<-1<-2 3->4->5->NULL
//         p c

// Third:
// nil<-1<-2<-3 4->5->NULL
//            p c

// Forth:
// nil<-1<-2<-3<-4 5->NULL
//               p c

// Fifth:
// nil<-1<-2<-3<-4<-5 NULL
//                  p  c
```
