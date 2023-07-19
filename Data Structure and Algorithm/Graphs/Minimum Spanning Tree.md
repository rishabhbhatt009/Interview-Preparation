# Minimum Spanning Tree
---
Definitions :
	- **Spanning Tree** : Connected sub-graph in an ==undirected graph==, where are all the vertices are connected by the ==minimum number of edges==. A graph can have multiple spanning trees.
	- **Minimum Spanning Tree** : A spanning tree with ==minimum total edge weights== in a ==weighted undirected graph==. A graph can have multiple minimum spanning tree.
	- **Cut Property** :  If you cut a graph into 2 sets. The edge with the minimum weight connecting 1 set to another will be in the MST

>[!Note] 
>A tree has no cycles, whereas a graph can have cycles.

Algorithms to construct a ==minimum spanning tree== of a ==weighted undirected graph== :
	- Kruskal’s algorithm  
	- Prim’s algorithm

---
## Kruskal's Algorithm
- Used to construct a ==minimum spanning tree (MST)== of a ==weighted undirected graph==.
- It uses a ==Greedy Algorithm== where it chooses the smallest available edge that does not make a cycle and adds to the tree.
- Therefore, expands the MST by adding edges.

### Steps
1. Sort all edges based on weight (ascending order) => ==Min Heap==
2. Pop the smallest edge
3. Connect vertices using the smallest edge - if it does not make a cycle
4. Connect N-1 times -> one common root for all N vertices

## Code

```python
def kruskals_algo(n:int, edges:List[List[int]]) -> int:
	# init
	UF = UnionFind(n)
	cost = 0 
	
	# 1. sorting 
	# Descending since we pop the last element = smallest
	# edges.sort(key = lambda x : x[2], reverse=True)
	
	# 2. min-heap
	heapq.heapify(edges) 
	# Implementation of min-head: 
	# - option 1 : edges => [cost, (a,b)], "cost" is the priority element
	# - option 2 : we can also create an class `Edge` and define `__lt__`
	
	while edges: 
		a, b, dist = heapq.heappop(edges) # edges.pop()
		
		if not UF.connected(a,b):
			UF.union(a,b)
			cost += dist 
			 
		if UF.root_nodes == 1:
			break 
	
	return cost
```

>[!Note]
>Time Complexity = $O(E*logE + E*\alpha(V)) = O(E*logE)$
>Space Complexity = $O(V)$

---
## Prim's Algorithm 
- Used to construct a ==minimum spanning tree (MST)== of a ==weighted undirected graph==.
- It uses a ==Greedy Algorithm== where it chooses the smallest edge that connects one set (visited) to the other (unvisited) and shifts the vertex to the visited set.
- Therefore, expands the MST by adding vertices.

### Steps 
1. Pick a vertex and add all its edges to a ==Min Heap==
2. Pop the smallest edge - Skip if the edges connect vertices that are visited
3. Add the connecting vertex to the visited set 
4. Add all its edges to the min heap (except the ones that connect to vertices in the visited set)
5. Repeat 2-3-4 until all vertices are visited

## Code 

1. Simple Prim's uses min-heap to get the edge with smallest wt. 

```python 
def mst_prims(self,N):
	
	# init 
	visited = set()
	not_visited = set(range(N)) # all nodes 
	cost = 0
	edge_set= []
	
	
	while len(visited) != N :
		
		# pick the smallest edge 
		if len(visited) == 0:
			dist, X, Y = 0, 0, 0 # first iteration 
		else :
			dist, X, Y = heapq.heappop(edge_set) # pop smallest edge by wt
		
		if Y in visited :
			continue 
			
		not_visited.remove(Y)
		visited.add(Y)
		cost += dist
		
		# add new edges to the set
		for node in range(N):
			if node not in visited :
				# dist = edge weight
				struct = (dist, Y, node)
				heapq.heappush(edge_heap, struct)
	
	return cost

```

>[!Note]
>Time Complexity : $O(N^2*log(N))$
>Space Complexity : $O(N^2+N) ~ O(N^2)$

2. Optimized Prim's 

```python
def prims_algo(n:int, edges:int)-> int:
	
	# init
	cost = 0 
	visited_nodes = 0
	visited = [False]*n # important : track visited nodes 
	min_edge = [float('inf')]*n # min available edge to node
	
	# boot at node 0
	min_edge[0] = 0
	
	while visited_nodes < N :
		curr_min_edge = float('inf')
		curr_node = -1 
		
		# pich the node with the smallest edge not visited
		for node in range(N):
			if node not visited[node] and curr_min_edge > min_edge[node] :
				curr_min_edge = min_edge[node]
				curr_node = node
	
		visited[curr_node] = True
		visited_nodes += 1
		cost += curr_min_edge
		
		# update min_edge from curr_node
		for node in range(N):
			weight = dist(curr_node, node)
			if node not visited[node] and min_edge[node] > weight:
				min_edge[node] = weight
	
	return cost
```

>[!Note]
>Time Complexity : $O(N * (N+N)) = O(N^2)$
>Space Complexity : $O(N+N) = O(N)$

---

## “Kruskal’s algorithm” v/s “Prim’s algorithm”

**Kruskal’s algorithm** expands the minimum spanning tree by **adding edges**. 
Whereas **Prim’s algorithm** expands the minimum spanning tree by **adding vertices**.