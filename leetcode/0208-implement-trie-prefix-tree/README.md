## Question

https://leetcode.com/problems/implement-trie-prefix-tree/

## Solutions

```go
type Node struct {
	isWord   bool
	children map[string]*Node
}


type Trie struct {
	root *Node
}

func getNode() *Node {
	return &Node{children: make(map[string]*Node)}
}

/** Initialize your data structure here. */
func Constructor() Trie {
	return Trie{getNode()}
}

/** Inserts a word into the trie. */
func (this *Trie) Insert(word string) {
	cur := this.root

	for _, w := range []rune(word) {
		c := string(w)
		if cur.children[c] == nil {
			cur.children[c] = getNode()
		}
		cur = cur.children[c]
	}

	cur.isWord = true
}

/** Returns if the word is in the trie. */
func (this *Trie) Search(word string) bool {
	cur := this.root

	for _, w := range []rune(word) {
		c := string(w)
		if cur.children[c] == nil {
			return false
		}
		cur = cur.children[c]
	}

	return cur.isWord
}

/** Returns if there is any word in the trie that starts with the given prefix. */
func (this *Trie) StartsWith(prefix string) bool {
	cur := this.root

	for _, w := range []rune(prefix) {
		c := string(w)
		if cur.children[c] == nil {
			return false
		}
		cur = cur.children[c]
	}

	return true
}
```
