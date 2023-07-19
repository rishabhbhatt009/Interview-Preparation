# Disjoint Set
---
Disjoint Set is a data structure/algorithm. The primary use is to address ==connectivity problems== between the components of a network. The main idea is that all connected vertices should have the same root node directly or indirectly. Therefore to check if two vertices are connected, we only need to check if they have the same root node.

There are 2 operations :
	1. **find** - returns the root node 
	2. **union** - connects two node 
	3. **connected** - returns `True` if nodes are connected 

## Optimized Disjoint 
>[!Explanation]+
>Optimized disjoint uses ==union by rank== and ==path compression==. 
>
>==union by rank== helps us create a balanced tree while the ==path compression== helps us connect a node to its root directly instead indirectly through a parent. The combined effect helps us achieve a time complexity of $O(\alpha(N)) = O(1)$ for find() and union().
>
>**Remember** : 
>	- **When to use this** : for connectivity problems where you ==do not care about the length of the path==. 
>	- **Clean up** : run find on all nodes at the end as it might be possible they are not pointing to their root node. You can mask it by making it count the number of roots.
>	- **Count Root Nodes** : Count starts at size and decrease every time 2 nodes with different root are connected. ==remember to use nonlocal== 

```python 
# Constructor 
root = list(range(size))
rank = [1] * size

# Path Compression
def find(X:int) -> int:
	if X != root[X]:
		root[X] = find(root[X])
	return root[X]

# Union by rank
def union(X:int, Y:int) -> None:
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

def connected(node1:int, node2:int) -> bool:
	return root[X] == root[Y]		

# Go through all edges and do union to create the data structure 
for (x,y) in edges :
	union(x,y)

# Clean Up or count number of roots 
def count_roots() -> set():
	root_nodes = set()
	for i in range(size):
		root_nodes.add(find(i))
```

^57dd16

>[!Time and Space Complexity]-
>constructor : $O(N)$
>find : $O(\alpha(N))$
>union : $O(\alpha(N))$
>connected : $O(\alpha(N))$
>
>Where $N$ is the number of vertices in the graph 
>Where $\alpha()$ is the **Inverse Ackermann Function** = O(1) in practice

---
## Other Algorithms 
| Algorithms       |   FIND    |   UNION   |  CONNECT  |
|:---------------- |:---------:|:---------:|:---------:|
| Quick Find       |   O(1)    |   O(N)    |   O(1)    |
| Quick Union      |   O(N)    |   O(N)    |   O(N)    |
| Union by Rank    | O(log(N)) | O(log(N)) | O(log(N)) |
| Path Compression | O(log(N)) | O(log(N)) | O(log(N)) |

### quick union is more efficient that quick find:
Time complexity for quick_union are worst case. Therefore to connect N elements the average time complexity for quick_find is $O(n^2)$ while that of quick_union is less than $O(n^2)$.

### union by rank helps us balance the tree:
When we do union by rank we generate a more ==balanced tree== with minimal height. This allows find() to run faster. 

## Revision
1. [The Earliest Moment When Everyone Become Friends](https://leetcode.com/explore/featured/card/graph/618/disjoint-set/3912/) 
2. [Optimize Water Distribution in a Village](https://leetcode.com/explore/featured/card/graph/618/disjoint-set/3916/) - this is not a good disjoint set application