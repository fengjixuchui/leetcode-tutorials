## Question

https://leetcode.com/problems/group-anagrams/

## Solutions

```go
package leetcode

import (
	"sort"
	"strings"
)

func SortString(w string) string {
	s := strings.Split(w, "")
	sort.Strings(s)
	return strings.Join(s, "")
}

func groupAnagrams(strs []string) [][]string {
	m := make(map[string][]string)

	for _, w := range strs {
		word := SortString(w)
		m[word] = append(m[word], w)
	}

	var ss [][]string
	for _, value := range m {
		ss = append(ss, value)
	}
	return ss
}
```
