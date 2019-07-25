## Question

https://leetcode.com/problems/word-ladder/

## Solutions

```go
func ladderLength(beginWord string, endWord string, wordList []string) int {
	// Change the wordList into a set.
	wordSet := make(map[string]bool, len(wordList))
	for _, word := range wordList {
		wordSet[word] = true
	}

	// Check if the endWord is inside the set.
	if !wordSet[endWord] {
		return 0
	}

	q := []string{beginWord}
	transformation := 0

	for len(q) != 0 {
		transformation++

		newQueue := []string{}
		for i := 0; i < len(q); i++ {
			word := q[i]
			for pos := 0; pos < len(word); pos++ {
				newWord := []rune(word)
				for ch := 'a'; ch <= 'z'; ch++ {
					newWord[pos] = ch
					s := string(newWord)
					if s == endWord {
						return transformation + 1
					}
					if wordSet[s] && s != word {
						newQueue = append(newQueue, s)
						wordSet[s] = false
					}
				}
			}
		}
		q = newQueue
	}

	return 0
}
```
