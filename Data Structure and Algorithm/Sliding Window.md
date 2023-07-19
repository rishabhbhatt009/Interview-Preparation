# Sliding Window 

**Identify** : Array or String questions that ask for optimal **subarray** or **substring** 

Types of sliding window problems : 
- Fixed size window 
- Dynamic size

---
## Fixed size sliding window 

given a window size find the optimal 

Intuition 
calculations + **auxiliary data structure** (map or stack) for complex calculations
reach the window : R+=1
slide the wind : L+=1 and R+=1

Code 

```python 
# init
L,R = 0,0 
# data-structure

while R<size :
	
	# calculate answer
	
	# increase window till you reack K (size of the window )
	if R-L+1 < k :
		R+=1
	
	# once you reach the window size 
	elif R-L+1 == k :
		
		# calculate / store optimal solution
		
		# calculation to remove L
		
		# slide window 		
		L+=1
		R+=1
```

---
## Dynamic sliding window 

Given a condition find the optimal size / all positives 

Intuition 
- Forming the condition is important :
	- sum == 5 or unique == k (k unique characters)
	- unique = window size all unique characters 
- conditions can be changed 

Code 

```python
# init
L,R = 0,0 
# data-structure

while R<size :
	
	# calculate answer
	
	if curr_ans < condition :
		# slide window : logic + calculation 
		R+=1
	
	elif curr_ans == condition : 
		# calculate / store optimal solution
		
		# slide window : logic + calculation 
		R+=1 
	
	elif curr_ans > condition :
		
		# slide window : logic + calculation 
		while curr_ans > condition :
			# calculation to remove L
			L+=1
		R+=1 
		
```

---
Resource : 
https://www.youtube.com/playlist?list=PL_z_8CaSLPWeM8BDJmIYDaoQ5zuwyxnfj

Problem : 
Longest Subarray with sum K | Postives and Negatives

