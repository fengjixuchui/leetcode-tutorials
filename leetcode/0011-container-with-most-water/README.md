## Question

https://leetcode.com/problems/container-with-most-water/

## Solutions

```go
// O(n) time | O(1) space
func maxArea(height []int) int {
	if len(height) < 2 {
		return 0
	}

	var maxArea = 0
	leftI, rightI := 0, len(height)-1

	for leftI < rightI {
		if height[leftI] > height[rightI] {
			area := (rightI - leftI) * height[rightI]
			if area > maxArea {
				maxArea = area
			}
			rightI--
		} else {
			area := (rightI - leftI) * height[leftI]
			if area > maxArea {
				maxArea = area
			}
			leftI++
		}
	}

	return maxArea
}
```
