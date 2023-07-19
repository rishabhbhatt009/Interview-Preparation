# Topological sorting

- Problem : Sorting items based on prerequisites
- Example : **selecting courses** for the semester in college, some advanced courses have prerequisites that require you to take some introductory courses first
- **Topological sorting** helps solve the problem. It provides a linear sorting based on the required ordering between vertices in directed acyclic graphs

- Algorithm : Khan's Algorithm 

---
## Khan's Algorithm 



### Code 

```python 
def create_graph (self, prereq):
	in_graph = collections.defaultdict(int)
	out_graph = collections.defaultdict(list)
	
	for x,y in prereq :
		in_graph[x] += 1
		out_graph[y].append(x)
	
	return {'in':in_graph, 'out':out_graph}
```

```python
def khans(self, N, graph):
			
	zero_degree_queue = []
	
	# add nodes with 0 in-degree to que
	for node in range(N):
		in_degree = graph['in'][node]
		if in_degree == 0 :
			zero_degree_queue.append(node)
			
	lst = []
	
	while zero_degree_queue : 
		
		curr_node = zero_degree_queue.pop(0)
		
		lst.append(curr_node)
		
		# reduce in-deree by one
		for node in graph['out'][curr_node]:
			graph['in'][node] -= 1
			if graph['in'][node] == 0 :
				zero_degree_queue.append(node)
		
	return lst
```

>[!Note]
>Time Complexity :  $O(E) + Q(V+E) = O(V+E)$
>Space Complexity : $O(E) + O(V) = O(V+E)$

### Limitation of the Algorithm

- Topological sorting only works with graphs that are **directed** and **acyclic**.
- There must be at **least one vertex in the “graph” with an “in-degree” of 0**. If all vertices in the “graph” have a non-zero “in-degree”, then all vertices need at least one vertex as a predecessor. In this case, no vertex can serve as the starting vertex.
