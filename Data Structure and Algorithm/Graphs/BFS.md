# BFS
Mainly used to :
	1. Traverse all nodes of a graph 
	2. ==SHORTEST PATH== b/w two nodes in a graph where all edges have equal and positive weights 

### **==QUEUE==** -> Auxiliary data structure used

> [!Note]
> DFS can also find the shortest path (in a graph where all edges have equal and positive weights) but has to traverse all paths before finding the shortest one. in BFS however, as soon as a path between the source vertex and target vertex is found, it is guaranteed to be the shortest path between the two nodes. Works like a **sonar**.

## Code 

Step 1 : Create a graph 

```python
import collections

# init
def __init__(self):
	self.graph : dict = collections.defaultdict(list)

# create graph
def create_graph(self, edges:list[list[int]]):
	for (x,y) in edges:
		self.graph[x].append(y)
		self.graph[y].append(x)
```

Step 2 : Traverse 

```python
# BFS-Traversal 
def bfs(self, source, dest):
	# BFS-Traversal 
	queue = [source] 
	visited = set()
	
	while queue:
		curr_node = queue.pop(0)
		
		if curr_node in visited:
			continue 
			
		if curr_node == dest :
			return True 
		
		for x in graph[curr_node]:
			queue.append(x)
		
		visited.add(curr_node)
	
	return False

def valid_path(n: int, edges: List[List[int]], source: int, dest: int) -> bool:
	# create the graph
	self.create_graph(edges)
	# DFS-Traversal 
	return self.bfs(source, dest)	
```

>[!Time and Space Complexity]
>Traveling all vertices :
>	- Time = $O(V+E)$
>	- Space = $O(V)$