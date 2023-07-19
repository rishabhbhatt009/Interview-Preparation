# Heap
---

- Priority Queue != Head
- Priority Queue (abstract) while heap is an actual data structure
- Heap is a Complete Binary Tree (CBT)
- Every node is >= (max-heap) or <= (min-heap) its children 

---
## Python Implementation 

- we use `heapq`
- converts the list to **min-heap** using `heapify()` 
- for **max-heap** make values (keys) negative


>[!Note]
>Time complexity of operations
>	-  make heap = `heapq.heapify` = $O(n)$
>	- push element = `heapq.heappush(heap,element)` = $O(log(n))$
>	- remove element = `heapq.heappop(heap)` = $O(log(n))$
>	- get min = `heap[0]` = $O(1)$

---
## Python Code 

```python
# importing library 
import heapq

#--------------------------------------------------------------
# vanilla min_heap
#--------------------------------------------------------------
lst = [1,2,4 ...]

# Operations 
heapq.heapify(lst) # convert lst to heap and store in itself
heapq.heappush(lst, element) # add val
heapq.heappop(heap) # pop min-val from top 

#--------------------------------------------------------------
print(heap) # heap is arranged in traversal order not ordered
print(lst[0]) # min element always

#--------------------------------------------------------------
# key based min heap
# - example : a min heap based on the len of list 
#--------------------------------------------------------------
lists = [[1,2,3], [1,2,3,4], [3]]
key = [len(lst) for lst in lists]

min_heap = list(zip(key,lst))
heapq.heapify(min_heap)

#--------------------------------------------------------------
```

---

![[Pasted image 20220619164356.png]]


>For Python, building a priority queue using heapify method takes $O(E)$ time, and we need $O(E*log(E))$ time for popping out all the elements from the priority queue. In total, we need $O(E*log(E))$ time in terms of Big-O notation.
