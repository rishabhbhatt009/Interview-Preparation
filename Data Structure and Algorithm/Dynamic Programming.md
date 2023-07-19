# Dynamic Programming
---

Characteristics of DP problems :
1. The problem can be broken into **subproblems**
2. The subproblems should **overlap** 
3. The problem has an **optimal substructure**

How is it different from other algorithm ?
1. **Greedy Algorithm** : has an optimal substructure, but subproblems are not **overlapping**
2. **Divide & Conquer** : break a problem down, but subproblems are not **overlapping**

---
## Intuition 

- Identify a dynamic problem 

- Think about 4 things :
	1. **State Variables** : defines a state
	2. **Function** / **Data structure** : holds the answer to sub-problems 
	3. **Base Cases** : pre-defined answers 
	4. **Recurrence Relation** : to move from one state to another

- Types of problems : 
	- **1-D Dynamic Programming** : 1 state variable is sufficient to define a state
	- **Multi Dimensional Dynamic Programming** : 2 or more state variable required 


---
## Implementing DP algorithm 

There are 2 implementation approaches :

1. Top-Down Approach (**Recursion + Memoization**) : 
	- implemented with recursion and made efficient with *memoization*
	- starts from the main problem, breaks it down recursively till we reach the base case 
	- Pro : easier to implement, more intuitive 
	- Cons : slower + recursion overhead

2. Bottom-Up Approach (**Tabulation**) : 
	- implemented with iteration 
	- starts at the base cases and moves towards the final solution 
	- Pro : faster as there is no recursion overhead 
	- Cons : you have to navigate in a specific order 


---
## Code 

Step 1 : Initialize the cost array and DPT

```python 
def __init__(self, cost):
	
	self.cost = [0] + cost # helps to align indexes 
	
	# init DPT
	self.DPT = hashmap/array 
	# add base cases to DPT 
	self.DPT[0] = constant 
	self.DPT[1] = constant 
```

Step 2 : DPT function based on implementation

Option 1 : Top-Down Approach (**Recursion + Memoization**) 

```python
def top_down(self, state_variables) : 
	
	# check if state exists in memory 
	if state_variable not in DPT :
		# recurrence relation
		option1 = 
		option2 = 
		self.DPT[state_variable] = combine(option1, option2) 
	
	return DPT[state_variable]
```

Option 2 : Bottom-Up Approach (**Tabulation**) 

```python 
def bottom_up(self) :
	
	# iterate through states in specific order
	for state_variable in range(base_case+1, final_state+1) : 
		# recurrence relation
		option1 = 
		option2 = 
		self.DPT[state_variable] = combine(option1, option2) 
	
	return DPT[final_state]	
```

>[!Note]
> Top_Down : we always use the **function** to get the answer 
> Bottom_Up : we use the **DPT** to get the answer

---
## Optimization :

- we need only n previous states to calculate the current state 
- n = number of choices