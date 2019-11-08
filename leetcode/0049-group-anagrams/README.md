## Question

https://leetcode.com/problems/group-anagrams/

## Solutions

```go
// O(n * nlogn) time | O(n) space
func groupAnagrams(strs []string) [][]string {
	if len(strs) == 0 {
		return [][]string{}
	}

	bucket := map[string][]string{}

	for _, str := range strs {
		b := []byte(str)
		sort.Slice(b, func(i, j int) bool {
			return b[i] < b[j]
		})
		key := string(b)
		bucket[key] = append(bucket[key], str)
	}

	result := [][]string{}
	for _, v := range bucket {
		result = append(result, v)
	}

	return result
}
```
