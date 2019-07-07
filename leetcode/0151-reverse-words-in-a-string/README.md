## Question

https://leetcode.com/problems/reverse-words-in-a-string/

## Solutions

```go
func reverse(char []rune, i, j int) []rune {
	for i < j {
		char[i], char[j] = char[j], char[i]
		i++
		j--
	}
	return char
}

func reverseWords(s string) string {
	if s == "" {
		return s
	}
	str := []rune(s)

	p, q, end := 0, 0, len(s)-1

	for end >= 0 && str[end] == ' ' {
		end--
	}
	for q <= end {
		start := p
		for q <= end && str[q] == ' ' {
			q++
		}
		for q <= end && str[q] != ' ' {
			str[p], str[q] = str[q], str[p]
			q++
			p++
		}
		reverse(str, start, p-1)
		if q <= end {
			str[p] = ' '
			p++
		}
	}

	reverse(str, 0, p-1)
	return string(str[0:p])
}
```
