## Question

https://leetcode.com/problems/maximum-binary-tree/

## Solutions

```go
func constructMaximumBinaryTree(nums []int) *TreeNode {
	if len(nums) == 0 {
		return nil
	}

	maxIdx := MaxIdx(nums)

	root := new(TreeNode)
	root.Val = nums[maxIdx]

	root.Left = constructMaximumBinaryTree(nums[:maxIdx])
	root.Right = constructMaximumBinaryTree(nums[maxIdx+1:])

	return root
}

func MaxIdx(nums []int) int {
	max := math.MinInt32
	maxIdx := 0
	for i := 0; i < len(nums); i++ {
		if nums[i] > max {
			max = nums[i]
			maxIdx = i
		}
	}
	return maxIdx
}
```
