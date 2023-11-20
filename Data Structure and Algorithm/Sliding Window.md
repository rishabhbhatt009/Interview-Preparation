# Sliding Window 

**Identify** : Array or String questions that ask for optimal **subarray** or **substring** 

Types of sliding window problems : 
- Fixed size window 
- Dynamic size

---
## Fixed size sliding window 

Given a window size find the optimal 

Intuition 
- calculations + ** auxiliary  data structure** (map or stack) for complex calculations
- reach the window : R+=1
- slide the wind : L+=1 and R+=1

Code 

```python 
# init
L,R = 0,0 
# data-structure

while R<size and R<len(lst) :
	# calculate answer
	...
	# increase window till you reack K (size of the window )
	if R-L+1 < k :
		R+=1
	# once you reach the window size 
	elif R-L+1 == k :
		# calculate / store optimal solution
		...
		# calculation to remove L
		...
		# slide window 		
		L+=1
		R+=1
```

---
## Dynamic sliding window 

Given a condition find the optimal size / all positives 

Intuition 
- Forming logic for valid window (**most important**) :
	- sum == 5 or unique == k (k unique characters)
	- unique = window size all unique characters 
- conditions can be changed (**do not understand**)

Code 

```python
# init
L,R = 0,0 
# data-structure

while R<size :
	# calculate answer
	...
	if curr_ans < condition :
		# calculate / store optimal solution
		...
		# increase window : logic + calculation 
		R+=1
	elif curr_ans == condition : 
		# calculate / store optimal solution
		...
		# slide window : logic + calculation 
		R+=1 
	elif curr_ans > condition :
		# slide window : logic + calculation 
		while curr_ans < condition :
			# calculation to remove L
			L+=1
		R+=1 
```

---
Resource : 
- https://www.youtube.com/playlist?list=PL_z_8CaSLPWeM8BDJmIYDaoQ5zuwyxnfj
- Problems : 
	- Longest Subarray with sum K | Postives and Negatives

---