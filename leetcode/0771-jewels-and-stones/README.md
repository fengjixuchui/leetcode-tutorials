## Question

https://leetcode.com/problems/jewels-and-stones/

## Solutions

```go
func numJewelsInStones(J string, S string) int {
	hash := make(map[rune]bool, len(J))

	for _, item := range J {
		hash[item] = true
	}

	counter := 0
	for _, item := range S {
		if _, ok := hash[item]; ok {
			counter++
		}
	}

	return counter
}
```
