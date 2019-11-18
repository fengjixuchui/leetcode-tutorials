## Question

https://leetcode.com/problems/group-anagrams/

## Solutions

```go
// O(n * nlogn) time | O(n) space
func groupAnagrams(strs []string) [][]string {
	res := [][]string{}

	if strs == nil || len(strs) == 0 {
		return res
	}

	mapping := make(map[string][]string)

	for _, str := range strs {
		b := []byte(str)
		sort.Slice(b, func(i, j int) bool {
			return b[i] < b[j]
		})
		mapping[string(b)] = append(mapping[string(b)], str)
	}

	for _, list := range mapping {
		res = append(res, list)
	}

	return res
}
```
