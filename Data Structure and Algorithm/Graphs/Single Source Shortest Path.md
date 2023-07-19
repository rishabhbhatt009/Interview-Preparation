# Single Source Shortest Path Problem

Algorithms : 
1. **BFS** : only works on ==unweighted graphs== 
2. **Dijkstra's algorithm** : only works on “single source shortest path” problem in a ==graph with non-negative weights==.
3. **Bellman-Ford algorithm** : solves the “single-source shortest path” in a ==weighted directed graph with any weights== (including negative weights).

---
## Dijkstra's Algorithm

### Intuition 

- We take the starting point as the center and gradually expand outward while updating the shortest path to reach other vertices
- uses a **greedy approach**, as each step selects the “minimum weight” from the currently reached vertices to find the “shortest path” to other vertices.

### Code 

Version-1 : use a 2-D table to store optimal cost and O(n) for min edge

```python
    self.table = {}
    
    def dijkstra(self, start):
        
        visited = set()
        self.table[start] = [0,-1] 
        
        while True :
	        # get shortest edge not visited 
            curr_node = self.shortest_edge(visited) 

            if curr_node == 0 :
                break 

            if curr_node in visited : 
                continue 
            
            # update time and add to queue
            for neighbor,wt in self.graph[curr_node].items() :
                cost = self.table[curr_node][0] + wt
                if self.table[neighbor][0] > cost : 
                    self.table[neighbor] = [cost, curr_node]
                
            visited.add(curr_node)
```

Version-2 : heap to store min_edge

```python
    def dijkstra(self, start, N):
        
        visited = set()
        heap = [[0,start]]
        heapq.heapify(heap)
        min_dist = collections.defaultdict(int)

        while heap :
            curr_cost, curr_node = heapq.heappop(heap)

            if curr_node in visited : 
                continue 
	        
	        visited.add(curr_node)
	        
            # update time and add to queue
            for neighbor,wt in self.graph[curr_node].items() :
                cost = curr_cost + wt
                if cost < min_dist[neighbor]:
	                min_dist[neighbor] = cost
                heapq.heappush(heap, [cost,neighbor])
	                
        return min_dist
```

>[!Note]
>Time Complexity : O(N+ElogN)

---
## Bellman-Ford Algorithm 

### Intuition

- acyclic graph : 
	- there are N-1 edges b/w 2 vertices 
	- max edges for shortest path = N-1

- cyclic graph with +ve cycle : 
	- max edges for shortest path N-1

- cyclic graph with -ve cycle : 
	- there exists no shortest path 
	- as the total keeps on decreasing every time we take the cycle
	- **then how does Bellman-Ford help ?** It can detect this -ve cycles 

### Code

![[Pasted image 20230717133347.png]]

>[!Note]
>Time = $O(k*E)$
>Space = $O(V)$
