## Question

https://leetcode.com/problems/course-schedule/

## Solutions

```go
func canFinish(numCourses int, prerequisites [][]int) bool {
	// key   is the courses we "need" to take
	// value is the courses we "want" to take
	graph := make(map[int][]int)
	// index is the courses we "want" to take
	// value is how many courses we "need" to take
	dependencies := make([]int, numCourses)

	for i := 0; i < len(prerequisites); i++ {
		want := prerequisites[i][0]
		need := prerequisites[i][1]

		dependencies[want]++

		if _, ok := graph[need]; ok {
			graph[need] = append(graph[need], want)
		} else {
			graph[need] = append([]int{}, want)
		}
	}

	// queue is the courses we can take now
	queue := make([]int, 0)
	for i := 0; i < numCourses; i++ {
		// dependencies == 0 means the course is not depend on other class
		if dependencies[i] == 0 {
			queue = append(queue, i)
		}
	}

	for len(queue) != 0 {
		course := queue[0]
		subClasses := graph[course]
		for i := 0; i < len(subClasses); i++ {
            dependencies[subClasses[i]]--
            // if there's no dependency for the subClasses means we can take the course now
			if dependencies[subClasses[i]] == 0 {
				queue = append(queue, subClasses[i])
			}
		}
		queue = queue[1:]
	}

	for i := 0; i < numCourses; i++ {
		if dependencies[i] != 0 {
			return false
		}
	}

	return true
}
```
