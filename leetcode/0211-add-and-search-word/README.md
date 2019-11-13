## Question

https://leetcode.com/problems/add-and-search-word-data-structure-design/

## Solutions

```go
type Node struct {
	val      byte
	children []*Node
	isEnd    bool
}

type WordDictionary struct {
	root *Node
}

/** Initialize your data structure here. */
func Constructor() WordDictionary {
	return WordDictionary{root: &Node{children: make([]*Node, 26)}}
}

/** Adds a word into the data structure. */
func (this *WordDictionary) AddWord(word string) {
	cur := this.root
	for i := 0; i < len(word); i++ {
		if cur.children[word[i]-'a'] == nil {
			cur.children[word[i]-'a'] = &Node{
				val:      word[i],
				children: make([]*Node, 26),
			}
		}
		cur = cur.children[word[i]-'a']
	}
	cur.isEnd = true
}

/** Returns if the word is in the data structure. A word could contain the dot character '.' to represent any one letter. */
func (this *WordDictionary) Search(word string) bool {
	return dfs(this.root.children, word, 0)

}

func dfs(root []*Node, word string, start int) bool {
	if start == len(word)-1 {
		if word[start] == '.' {
			for _, r := range root {
				if r != nil && r.isEnd {
					return true
				}
			}
			return false
		}
		return root[word[start]-'a'] != nil && root[word[start]-'a'].isEnd
	}

	if word[start] == '.' {
		for _, r := range root {
			if r != nil && dfs(r.children, word, start+1) {
				return true
			}
		}
		return false
	}

	if root[word[start]-'a'] != nil {
		return dfs(root[word[start]-'a'].children, word, start+1)
	}

	return false
}
```

## Tutorials

- https://www.youtube.com/watch?v=GLnEtY8_9S0
