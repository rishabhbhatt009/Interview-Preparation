# Graphs 
---
## Topics 



---
Graph is a ==non-linear data structure==

## Introduction
*Types of graphs :*
	- Undirected 
	- Directed 
		- Cyclic 
		- Acyclic ~ [[Trees]] also called as DAG
	- *Weighted Graph* 

*Terms Associated :*
	- vertex / vertices
	- edge 
	- paths => sequence of edges
	- path length => # of edges
	- cycle 
	- *negative weighted cycle*
	- connectivity 
	- degree
		- in degree 
		- out degree 

---
## Representation

```python 
# 1. adjacency matrix
graph = [[0, 2, 0], 
		 [2, 0, 3], 
		 [0, 3, 0]]

# 2. adjacency list
graph = { 
		 0: {1: 2}, 
		 1: {0: 2, 2: 3}, 
		 2: {1: 3} 
		 }

# 3. edge list : 
graph = [ 
		 (0, 1, 2), 
		 (1, 0, 2), 
		 (1, 2, 3), 
		 (2, 1, 3) 
		 ]
```

---
## Topics :
1. [[Disjoint Set]]
2. [[BFS]] - [[DFS]]
3. [[Minimum Spanning Tree]] 
4. [[Single Source Shortest Path]]
5. [[Topological Sorting]]

TAGS : #DSA-TOPIC

---