## Question

https://leetcode.com/problems/implement-trie-prefix-tree/

## Solutions

```go
type Node struct {
	val      byte
	children []*Node
	isEnd    bool
}

type Trie struct {
	root *Node
}

func Constructor() Trie {
	return Trie{
		root: &Node{
			children: make([]*Node, 26),
		},
	}
}

func (this *Trie) Insert(word string) {
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

func (this *Trie) Search(word string) bool {
	cur := this.root
	for i := 0; i < len(word); i++ {
		if cur.children[word[i]-'a'] == nil {
			return false
		}
		cur = cur.children[word[i]-'a']
	}
	return cur.isEnd
}

func (this *Trie) StartsWith(prefix string) bool {
	cur := this.root
	for i := 0; i < len(prefix); i++ {
		if cur.children[prefix[i]-'a'] == nil {
			return false
		}
		cur = cur.children[prefix[i]-'a']
	}
	return true
}
```

### Tutorials

- https://www.youtube.com/watch?v=pkaooVBexeU
