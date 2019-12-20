## Question

https://leetcode.com/problems/delete-node-in-a-linked-list/

## Solutions

```go
// T: O(1), S: O(1)
func deleteNode(node *ListNode) {
	node.Val = node.Next.Val
	node.Next = node.Next.Next
}
```
