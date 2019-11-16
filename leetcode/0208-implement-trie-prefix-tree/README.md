## Question

https://leetcode.com/problems/implement-trie-prefix-tree/

## Solutions

```go
type Trie struct {
	children []*Trie
	word     string
}

func Constructor() Trie {
	return Trie{children: make([]*Trie, 26)}
}

func (this *Trie) Insert(word string) {
	root := this
	for i := 0; i < len(word); i++ {
		if root.children[word[i]-'a'] == nil {
			root.children[word[i]-'a'] = &Trie{children: make([]*Trie, 26)}
		}
		root = root.children[word[i]-'a']
	}
	root.word = word
}

func (this *Trie) Search(word string) bool {
	root := this
	for i := 0; i < len(word); i++ {
		if root.children[word[i]-'a'] == nil {
			return false
		}
		root = root.children[word[i]-'a']
	}
	return root.word == word
}

func (this *Trie) StartsWith(prefix string) bool {
	root := this
	for i := 0; i < len(prefix); i++ {
		if root.children[prefix[i]-'a'] == nil {
			return false
		}
		root = root.children[prefix[i]-'a']
	}
	return true
}
```

### Tutorials

- https://www.youtube.com/watch?v=pkaooVBexeU
