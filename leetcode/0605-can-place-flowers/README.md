## Question

https://leetcode.com/problems/can-place-flowers/

## Solutions

```go
func canPlaceFlowers(flowerbed []int, n int) bool {
	// [0]
	if len(flowerbed) == 1 && flowerbed[0] == 0 {
		flowerbed[0] = 1
		n--
	}

	// [0,0,1]
	if flowerbed[0] == 0 && flowerbed[1] == 0 {
		flowerbed[0] = 1
		n--
	}

	for i := 1; i < len(flowerbed); i++ {
		if flowerbed[i] == 0 {
			if flowerbed[i-1] == 0 && i == len(flowerbed)-1 {
				flowerbed[i] = 1
				n--
				continue
			}
			if flowerbed[i-1] == 0 && flowerbed[i+1] == 0 {
				flowerbed[i] = 1
				n--
			}
		}

	}
	return n <= 0
}
```
