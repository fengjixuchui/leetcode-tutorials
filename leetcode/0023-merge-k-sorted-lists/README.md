## Question

https://leetcode.com/problems/merge-k-sorted-lists/

## Solutions

```go
// Time: O(m*n*lon(m*n)), Space: O(m*n)
func mergeKLists(lists []*ListNode) *ListNode {
	if lists == nil || len(lists) == 0 {
		return nil
	}

	nodes := []*ListNode{}

	for i := 0; i < len(lists); i++ {
		head := lists[i]
		for head != nil {
			node := head
			head = head.Next
			node.Next = nil
			nodes = append(nodes, node)
		}
	}

  if len(nodes) == 0 {
    return nil
  }

	sort.Slice(nodes, func(i, j int) bool {
		return nodes[i].Val < nodes[j].Val
	})

	dummy := &ListNode{}
	head := nodes[0]
	dummy.Next = head

	for i := 1; i < len(nodes); i++ {
		head.Next = nodes[i]
		head = head.Next
	}

	return dummy.Next
}
```

## Tutorials

- https://www.youtube.com/watch?v=zLcNwcR6yO4
