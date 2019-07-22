## Question

https://leetcode.com/problems/0107-binary-tree-level-order-traversal-ii/

## Solutions

```go
func levelOrderBottom(root *TreeNode) [][]int {
	if root == nil {
		return make([][]int, 0)
	}

	currLevel := []*TreeNode{}
	nextLevel := []*TreeNode{}
	ans := [][]int{}

	currLevel = append(currLevel, root)

	for len(currLevel) != 0 {
		// currLevelElem stores the current level values.
		currLevelElem := make([]int, 0)

		for i := 0; i < len(currLevel); i++ {
			node := currLevel[i]
			// Get the next nevel nodes.
			currLevelElem = append(currLevelElem, node.Val)
			if node.Left != nil {
				nextLevel = append(nextLevel, node.Left)
			}
			if node.Right != nil {
				nextLevel = append(nextLevel, node.Right)
			}
		}

		// Prepend the item
		ans = append([][]int{currLevelElem}, ans...)

		currLevel = nextLevel
		// Reset value for the next round.
		nextLevel = []*TreeNode{}
	}

	return ans
}
```
