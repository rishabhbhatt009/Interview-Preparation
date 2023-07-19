# Smallest String With Swaps
![[Pasted image 20220617002831.png]] 

## Explanation 
We create a [[Disjoint Set]] data structure. All nodes with a common root can be arranged in any way as we have ==unlimited swaps==. 
1. Connect all nodes 
2. Create a hash map with roots as keys and the char of all its children (including root) as values. This also ==masks the  clean up==
3. Sort the values of each root
4. Create a new string and pull the lexicographically smallest element from it root while also removing/poping the smallest char from hash map every time 
 
```python
# Write solution
def smallestStringWithSwaps(self, s: str, pairs: List[List[int]]) -> str:
	
	# edge case 
	if len(s) == 1:
		return s
	
	# init
	root = list(range(len(s)))
	rank = [1] * len(s)
	
	# find -> returns the root of the node (path compression)
	def find(x:int) -> int:
		if root[x] == x:
			return x 
		
		root[x] = find(root[x])
		return root[x]
	
	# union by rank -> connects 2 nodes
	def union(x:int, y:int) -> None:
		rootx = find(x)
		rooty = find(y)
		
		if rootx != rooty:
			if rank[rootx] > rank[rooty]:
				root[rooty] = rootx
			elif rank[rooty] > rank[rootx]:
				root[rootx] = rooty
			else:
				root[rooty] = rootx
				rank[rootx] += 1
	
	# connect all nodes
	for (x,y) in pairs:
		union(x,y)
	
	# create a hash
	root_nodes = {}
	for x in range(len(s)):
		rootx = find(x)
		
		if rootx not in root_nodes: 
			root_nodes[rootx] = [s[x]]
		else:
			root_nodes[rootx].append(s[x])
	
	for x in root_nodes: 
		root_nodes[x].sort()
	
	ret = []
	for i in range(len(s)):
		rooti = find(i)
		ret.append(root_nodes[rooti][0])
		root_nodes[rooti].pop(0)
	
	return ''.join(ret)
```

>[!Time and Space Complexity]+
>1. To create the disjoint set data structure we iterate through all edges and do a union operation = $E * O(\alpha(V))$ 
>2. Create hash map = $V * O(\alpha(V))$
>3. Sort each values at each root node = $V * O(n*log(N))$
>4. Create return string = $V$
>
>Time Complexity = $O((E+V) * \alpha(V) + V * (n*log(N)) + V)$
>Space Complexity = $O(V)$
>
>Where E = number of edges, V = number of vertices, ==$\alpha()$ = Inverse Ackermann Function==

## References 
1. [Link to the question](https://leetcode.com/explore/featured/card/graph/618/disjoint-set/3913/)
2. [[Disjoint Set]]
3. TAGS : #Leetcode