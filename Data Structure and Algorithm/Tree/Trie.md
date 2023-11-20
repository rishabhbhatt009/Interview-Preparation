# Trie

**Trie**, also called **prefix tree**, is a special form of a Nary tree, typically used to ==store strings== 

One important property of Trie is that all the descendants of a node have a common prefix of the string associated with that node. That's why Trie is also called `prefix tree`.

Structure of a trie :
- **paths** represent different characters
- node represents a **string (prefix)**, each node might have several children nodes 
- **child nodes** represent strings = **origin string** (prefix from parent) + **character** on the path
- root node represents `null` ~ empty string

Trie is widely used in various applications, such as autocomplete, spell checker, etc.

---
## Code 

Trie node structure : 
- we can **represent the children nodes** in Trie node with an Array / Hashmap 
- each Trie node represents a string but not all the strings are meaningful words. If we only want to store words in a Trie, we might declare a boolean in each node as a flag to indicate if **the string represented by this node is a word or not**

```python
class TrieNode:
    def __init__(self, char = ""):
        self.string = char
        self.children = {}
        self.is_end = False
        # word end counter 
        # self.counter = 0
```

Trie Operations :

```python
class Trie:
	
	# initialize your data structure
    def __init__(self):
        self.root = TrieNode()
	
    
    # insert nodes 
    def insert(self, word: str) -> None:
	    # init to root node 
        node = self.root
        # iterate through the string 
        for char in word:
	        if char not in node.children :
		        new_node = TrieNode(char)
                node.children[char] = new_node
			node = node.children[char]
		
		# mark the end of a string 
        node.is_end = True 
        # node.counter += 1 # indicate the end of multiple strings maybe
    
	
	# check if the word exists in the triem
    def search(self, word: str) -> bool:
        # init to root node 
        node = self.root
        # iterate through the string 
        for char in word:
            if char not in node.children:
                return False
            node = node.children[char]
        
        # Reached the end of word
        
        # Variation 1. Search for prefix 
        # return True 
        
        # Variation 2. Search for word 
        # return True if word is present, i.e is_end = True else False
        return node.is_end
```

>[!Warning]
>- don't forget to set is_word when inserting 
>- don't forget to set val when inserting
>

> [!Note]
> Time Complexity 
> Search, Insertion and Deletion = $O(M)$, where M is the maximum length of a word
> 
> Space Complexity for a Trie
> $O (M*N)$ - M is maximum length of a word and N is number of words
> This is the worst case, complexity improves when more words overlap  
> 

---
## Optimization 

- Search : Store max length at each node, if the length of search word > max length of node return False 

---