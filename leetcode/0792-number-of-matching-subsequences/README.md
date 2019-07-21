## Question

https://leetcode.com/problems/number-of-matching-subsequences/

## Solutions

```go
// Example
// S = "abcde"
// words = ["a", "bb", "acd", "ace"]
func numMatchingSubseq(S string, words []string) int {
	count := 0
	wordDict := make(map[byte][]string)

	for i := 0; i < len(words); i++ {
		word := words[i]
		wordDict[word[0]] = append(wordDict[word[0]], word)
	}

	// wordDict: [
	// 	"a": ["a", "acd", "ace"],
	//  "b": ["bb"]
	// ]

	for i := 0; i < len(S); i++ {
		char := S[i]
		wordsBeginWithChar := wordDict[char]
		// reset
		wordDict[char] = []string{}

		for j := 0; j < len(wordsBeginWithChar); j++ {
			word := wordsBeginWithChar[j]
			if len(word) == 1 {
				count++
			} else {
				wordDict[word[1]] = append(wordDict[word[1]], word[1:])
			}
		}
	}

	return count
}
```
