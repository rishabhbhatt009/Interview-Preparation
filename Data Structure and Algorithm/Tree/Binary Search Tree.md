# BST

---
Properties of BST 
Logic for adding a node : [link](https://leetcode.com/problems/insert-into-a-binary-search-tree/editorial/)
Logic for deleting a node : [link](https://leetcode.com/problems/delete-node-in-a-bst/editorial/)

---
Time Complexity : 
- Searching : log(N)
- Adding  a node : O(H)
- Deleting a node : O(H)

Note : 
- where H is a height of the binary tree. 
- H=log⁡N for the **balanced tree** and H=N for a **skewed tree**

---
Delete Node 

```python 
def deleteNode(self, root: Optional[TreeNode], key: int):
	if not node :
		return None
	if node.val == key :
		if node.left and node.right :
			# find successor and successor's predecessor
			prev,curr = None,node.right
			while curr.left :
				prev = curr
				curr = curr.left
			# detach 
			if prev : prev.left = None
			# insert
			if node.left : curr.left = node.left
			if prev : curr.right = node.right
			return curr
		elif node.left or node.right :
			node = node.left if node.left else node.right    
		else :
			node = None
	elif node.val < key :
		node.right = self.deleteNode(node.right,key)
	else :
		node.left = self.deleteNode(node.left,key)
	return node
```

---
