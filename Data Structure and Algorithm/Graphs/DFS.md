# DFS
Mainly used to :
	1. Traverse all vertices in a graph 
	2. Traverse all path between 2 vertices in a graph 

### **==STACK==** -> Auxiliary data structure used
1. list in the form of stack which follows LIFO
2. recursion stack 

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
# DFS-Traversal 
def dfs(self, source:int, dest:int):
	stack = [source] 
	visited = set()
	
	while stack:
		curr_node = stack.pop()
	
		if curr_node in visited:
			continue
		
		if curr_node == dest :
			return True 
		
		for x in self.graph[curr_node]:
			stack.append(x)
		
		visited.add(curr_node)
	
	return False

def valid_path(n: int, edges: List[List[int]], source: int, dest: int) -> bool:
	# create the graph
	self.create_graph(edges)
	# DFS-Traversal 
	return self.dfs(source, dest)
```

>[!Time and Space Complexity]
>Traveling all vertices :
>	- Time = $O(V+E)$
>	- Space = $O(V)$
>
>Traveling all paths
>	- Time = $O((V-1)!)$
>	- Space = $O(V^3)$

When you want to **record path traversed** :
Code modification : simply store path in the `stack` instead of `curr_node` to track it

```python
def dfs(self, graph, start, dest):

	stack = [[start]] # the stack holds the path 
	paths = [] # list of paths 

	while stack :
		path = stack.pop()
		curr_node = path[-1]

		if curr_node == dest:
			paths.append(path)

		for node in graph[curr_node]:
			# check if node is visited 
			if node not in path :
				new_path = path + [node]
				stack.append(new_path)

	return paths
```

> [!Warning]
> `path` shouldn't be stored as a `set` as sets are unordered which will result in bizarre paths. Therefore it should always be stored as list 