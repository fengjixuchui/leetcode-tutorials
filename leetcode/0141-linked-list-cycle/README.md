## Question

https://leetcode.com/problems/linked-list-cycle/

## Solutions

HashTable:

```go
func hasCycle(head *ListNode) bool {
	visited := map[*ListNode]bool{}

	for head != nil {
		if visited[head] {
			return true
		}
		visited[head] = true
		head = head.Next
	}

	return false
}
```

Two Pointers:

```go
// Time: O(n), Space: O(1)
func hasCycle(head *ListNode) bool {
	if head == nil {
		return false
	}

	slow, fast := head, head.Next

	for fast != nil && fast.Next != nil {
		slow = slow.Next
		fast = fast.Next.Next
    if slow == fast {
          return true
    }
	}

	return false
}
```
