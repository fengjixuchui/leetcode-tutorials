## Question

https://leetcode.com/problems/binary-tree-level-order-traversal/

## Solutions

```go
func levelOrder(root *TreeNode) [][]int {
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

		// Loop throuht all node in current level.
		for i := 0; i < len(currLevel); i++ {
			node := currLevel[i]
			currLevelElem = append(currLevelElem, node.Val)

			// Get the next nevel nodes.
			if node.Left != nil {
				nextLevel = append(nextLevel, node.Left)
			}
			if node.Right != nil {
				nextLevel = append(nextLevel, node.Right)
			}
		}

		ans = append(ans, currLevelElem)
		// We are going to the next level so we set the nextLevel as currLevel.
		currLevel = nextLevel
		// Reset value for the next round.
		nextLevel = []*TreeNode{}
	}

	return ans
}
```
