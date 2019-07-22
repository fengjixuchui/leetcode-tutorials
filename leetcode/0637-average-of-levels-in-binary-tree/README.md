## Question

https://leetcode.com/problems/average-of-levels-in-binary-tree/

## Solutions

```go
func averageOfLevels(root *TreeNode) []float64 {
	currLevel := []*TreeNode{}
	nextLevel := []*TreeNode{}
	ans := []float64{}

	currLevel = append(currLevel, root)

	for len(currLevel) != 0 {
		levelSum := 0

		// Loop throuht all node in current level.
		for i := 0; i < len(currLevel); i++ {
			currNode := currLevel[i]
			levelSum += currNode.Val

			// Get the next nevel nodes.
			if currNode.Left != nil {
				nextLevel = append(nextLevel, currNode.Left)
			}
			if currNode.Right != nil {
				nextLevel = append(nextLevel, currNode.Right)
			}
		}

		ans = append(ans, float64(levelSum)/float64(len(currLevel)))
		// We are going to the next level so we set the nextLevel as currLevel.
		currLevel = nextLevel
		// Reset value for the next round.
		nextLevel = []*TreeNode{}
	}

	return ans
}
```
