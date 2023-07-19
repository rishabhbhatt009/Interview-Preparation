# Number of Provinces
![[Pasted image 20220617002951.png]]

## Explanation 
We create a [[Disjoint Set]] data structure. At the end of all unions. We count the number of distinct root nodes and mask the clean up with it.

Check out the `nonlocal` used in union 

```python
# code from countComponents
def countComponents(self, N: int, edges: List[List[int]]) -> int:
	if n == 1:
		return 1
	
	# init DS
	root = list(range(N))
	rank = [1]*N
	root_nodes = n
	
	# find with path compression
	def find(X): 
		if root[X] == X:
			return X
		root[X] = find(root[X])
		return root[X]
	
	def union(X,Y):
		nonlocal root_nodes 
		rootX = find(X)
		rootY = find(Y)
		
		if rootX != rootY:
			if rank[rootX] > rank[rootY]:
				root[rootY] = rootX
			elif rank[rootY] > rank[rootX]:
				root[rootX] = rootY
			else:
				root[rootY] = rootX
				rank[rootX] += 1
			root_nodes -= 1
	
	for (i,j) in edges:
		union(i,j)
	
	return (root_nodes)
```

>[!Time and Space Complexity]-
>Discuss the time and space complexity 

## References 
1. Link to the question
2. [[BFS]] / [[DFS]]
3. [[Disjoint Set]]
4. TAGS : #Leetcode