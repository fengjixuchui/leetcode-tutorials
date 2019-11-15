## Question

https://leetcode.com/problems/kth-smallest-element-in-a-bst/

## Solutions

```go
// O(n) time | O(n) space
func kthSmallest(root *TreeNode, k int) int {
	queue := []int{}
	dfs(root, &queue)
	for i := 0; i < k-1; i++ {
		queue = queue[1:]
	}
	return queue[0]
}

func dfs(root *TreeNode, queue *[]int) {
	if root == nil {
		return
	}
	dfs(root.Left, queue)
	*queue = append(*queue, root.Val)
	dfs(root.Right, queue)
}
```

## Tutorials

- https://www.youtube.com/watch?v=y9GhePWGVNU
