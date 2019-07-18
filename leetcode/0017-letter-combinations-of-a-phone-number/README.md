## Question

https://leetcode.com/problems/letter-combinations-of-a-phone-number/

## Solutions

```go
var mapping = []string{
	"abc",
	"def",
	"ghi",
	"jkl",
	"mno",
	"pqrs",
	"tuv",
	"wxyz",
}

func bt(digits string, start int, str string, results *[]string) {
	if len(str) == len(digits) {
		*results = append(*results, str)
		return
	}

	chars := mapping[digits[start]-'2']

	for i := 0; i < len(chars); i++ {
		bt(digits, start+1, str+string(chars[i]), results)
	}
}

func letterCombinations(digits string) []string {
	if len(digits) == 0 {
		return []string{}
	}
	results := make([]string, 0)
	bt(digits, 0, "", &results)
	return results
}
```
