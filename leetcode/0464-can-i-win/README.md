## Question

https://leetcode.com/problems/can-i-win/

## Solutions

```go
func dfs(state []int, desiredTotal int, hashMap map[string]bool) bool {
	key := IntToString(state)
	if _, ok := hashMap[key]; ok {
		return hashMap[key]
	}

	for i := 1; i < len(state); i++ {
		if state[i] == 0 {
			state[i] = 1
			if desiredTotal-i <= 0 || !dfs(state, desiredTotal-i, hashMap) {
				hashMap[key] = true
				state[i] = 0
				return true
			}
			state[i] = 0
		}
	}
	hashMap[key] = false
	return false
}

func canIWin(maxChoosableInteger int, desiredTotal int) bool {
	if ((1+maxChoosableInteger)*maxChoosableInteger)/2 < desiredTotal {
		return false
	}
	// state tracks if the number is used or not
	state := make([]int, maxChoosableInteger+1)
	hashMap := map[string]bool{}
	return dfs(state, desiredTotal, hashMap)
}

func IntToString(ints []int) string {
	b := ""
	for _, v := range ints {
		if len(b) > 0 {
			b += ","
		}
		b += strconv.Itoa(v)
	}
	return b
}
```
