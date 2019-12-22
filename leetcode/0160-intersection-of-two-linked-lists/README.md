## Question

https://leetcode.com/problems/intersection-of-two-linked-lists/

## Solutions

```go
// Time: O(m+n), Space: O(1)
func getIntersectionNode(headA, headB *ListNode) *ListNode {
	lengthA := getLength(headA)
	lengthB := getLength(headB)

	var lengthDiff int
	var list1, list2 *ListNode
	if lengthA > lengthB {
		lengthDiff = lengthA - lengthB
		list1 = headA
		list2 = headB
	} else {
		lengthDiff = lengthB - lengthA
		list1 = headB
		list2 = headA
	}

	for lengthDiff != 0 {
		list1 = list1.Next
		lengthDiff--
	}

	for list1 != nil {
		if list1 == list2 {
			return list1
		}
		list1 = list1.Next
		list2 = list2.Next
	}

	return nil
}

func getLength(head *ListNode) int {
	length := 0
	for head != nil {
		length++
		head = head.Next
	}
	return length
}
```
