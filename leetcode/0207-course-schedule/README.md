## Question

https://leetcode.com/problems/course-schedule/

## Solutions

```go
// Time: O(n), Space: O(n)
func canFinish(numCourses int, prerequisites [][]int) bool {
	indegree := make([]int, numCourses)
	edges := make([][]int, numCourses)

	for i := 0; i < len(prerequisites); i++ {
		edges[prerequisites[i][1]] = append(edges[prerequisites[i][1]], prerequisites[i][0])
		indegree[prerequisites[i][0]]++
	}

	queue := []int{}
	for i := 0; i < len(indegree); i++ {
		if indegree[i] == 0 {
			queue = append(queue, i)
		}
	}

	var count int
	for len(queue) != 0 {
		course := queue[0]
		queue = queue[1:]
		count++

		n := len(edges[course])
		for i := 0; i < n; i++ {
			edge := edges[course][i]
			indegree[edge]--

			if indegree[edge] == 0 {
				queue = append(queue, edge)
			}
		}
	}

	return count == numCourses
}
```

## Tutorials

- https://www.youtube.com/watch?v=m9jUbHKQjGc
