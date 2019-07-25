## Question

https://leetcode.com/problems/different-ways-to-add-parentheses/

## Solutions

```go
func diffWaysToCompute(input string) []int {
	return ways(input, map[string][]int{})
}

func ways(input string, cache map[string][]int) []int {
	if _, ok := cache[input]; ok {
		return cache[input]
	}

	fns := map[rune]func(x, y int) int{
		'+': func(x, y int) int { return x + y },
		'-': func(x, y int) int { return x - y },
		'*': func(x, y int) int { return x * y },
	}

	ans := []int{}

	for i := 0; i < len(input); i++ {
		ch := input[i]

		if ch == '+' || ch == '-' || ch == '*' {
			left := input[:i]
			right := input[i+1:]

			l := ways(left, cache)
			r := ways(right, cache)

			f := fns[rune(ch)]

			for _, a := range l {
				for _, b := range r {
					// calculate all the combination
					ans = append(ans, f(a, b))
				}
			}
		}
	}

	// input is a single number
	if len(ans) == 0 {
		number, _ := strconv.Atoi(input)
		ans = append(ans, number)
	}

	// store in the cache before return the answer.
	cache[input] = ans

	return ans
}
```
