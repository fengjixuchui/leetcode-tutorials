## Question

https://leetcode.com/problems/robot-bounded-in-circle/

## Solutions

```go
func isRobotBounded(instructions string) bool {
	degree := 0
	cx, cy := 0, 0

	instructions += instructions + instructions + instructions

	for i := 0; i < len(instructions); i++ {
		in := instructions[i]

		if in == 'L' {
			if degree == 0 {
				degree = 270
			} else {
				degree -= 90
			}
			continue
		}
		if in == 'R' {
			if degree == 270 {
				degree = 0
			} else {
				degree += 90
			}
			continue
		}

		if in == 'G' {
			switch degree {
			case 0:
				cx++
			case 90:
				cy++
			case 180:
				cx--
			case 270:
				cy--
			}
		}
	}

	return cx == 0 && cy == 0
}
```
