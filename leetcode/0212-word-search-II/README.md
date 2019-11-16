## Question

https://leetcode.com/problems/word-search-ii/

## Solutions

```go
type Node struct {
	children []*Node
	word     string
}

func New() *Node {
	return &Node{children: make([]*Node, 26)}
}

func (this *Node) Insert(word string) {
	root := this
	for i := 0; i < len(word); i++ {
		if root.children[word[i]-'a'] == nil {
			root.children[word[i]-'a'] = &Node{children: make([]*Node, 26)}
		}
		root = root.children[word[i]-'a']
	}
	root.word = word
}

func findWords(board [][]byte, words []string) []string {
	res := []string{}
	if board == nil || len(board) == 0 {
		return res
	}
	root := New()
	for _, word := range words {
		root.Insert(word)
	}
	for i := 0; i < len(board); i++ {
		for j := 0; j < len(board[0]); j++ {
			c := board[i][j]
			if root.children[c-'a'] != nil {
				dfs(board, i, j, root, &res)
			}
		}
	}
	return res
}

func dfs(board [][]byte, i, j int, root *Node, res *[]string) {
	if i < 0 || j < 0 || i >= len(board) || j >= len(board[0]) {
		return
	}

	c := board[i][j]
	if c == '*' || root.children[c-'a'] == nil {
		return
	}

	cur := root.children[c-'a']
	if cur.word != "" {
		(*res) = append(*res, cur.word)
		cur.word = ""
	}

	board[i][j] = '*'
	dfs(board, i+1, j, cur, res)
	dfs(board, i-1, j, cur, res)
	dfs(board, i, j+1, cur, res)
	dfs(board, i, j-1, cur, res)
	board[i][j] = c
}
```

## Tutorials

- https://www.youtube.com/watch?v=rSDG7mlk5iQ
