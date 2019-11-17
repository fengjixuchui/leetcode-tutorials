## Question

https://leetcode.com/problems/binary-tree-inorder-traversal/

## Solutions

```go
// Time: O(n), Space: O(n)
func inorderTraversal(root *TreeNode) []int {
	res := []int{}

	if root == nil {
		return res
	}

	stack := []*TreeNode{}

	for root != nil || len(stack) != 0 {
		for root != nil {
			stack = append(stack, root)
			root = root.Left
		}

		last := stack[len(stack)-1]
		stack = stack[:len(stack)-1]
		res = append(res, last.Val)

		root = last.Right
	}

	return res
}
```

```go
// Time: O(n), Space: O(n)
func inorderTraversal(root *TreeNode) []int {
	res := []int{}

	if root == nil {
		return res
	}
	dfs(root, &res)

	return res
}

func dfs(root *TreeNode, res *[]int) {
	if root == nil {
		return
	}
	dfs(root.Left, res)
	*res = append(*res, root.Val)
	dfs(root.Right, res)
}
```
