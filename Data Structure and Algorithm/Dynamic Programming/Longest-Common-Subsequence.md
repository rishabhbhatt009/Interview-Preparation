# Longest Common Subsequence

---
Concept
- **Solution Flow** : Recursive -> Memoization -> Top-Down 
- **Substring** (continuous) v/s **Subsequence** (not continuous but in-order)
- For a recursive problem we need to answer : 
	1. how do we make the **I/P smaller** ? 
		- we have 2 strings s1 and s2. 
		- for top-down we start at the largest I/P and break it down 
		- therefore we need to dec the I/P for each rec. call 
	2. what are the **base condition** ? 
		- think about the smallest valid I/P
		- when s1 and s2 reach 0
	3. **choice diagram** ? 

---
Top-Down

```python 
# input
s1 : str = 'string1'
s2 : str = 'string2'

# init (the base case condition takes care of init base cases)
N,M = len(s1), len(s2) # dont get bogged down my N,M instead of M,N
DPT : dict = dict()
# DPT : list[list] = [[0]*(M+1) for _ in range(N+1)]

def top_down (i:int, j:int) -> int :
	# base case 
	if i==0 or j==0 : 
		return 0
	# check in mem
	if (i,j) in DPT : 
		return DPT[i,j]
	# choices
	if s1[i] == s2[j] :
		DPT[i,j] = 1+LCS(i-1,j-1)
	else :
		ch1 = LCS(i-1,j)
		ch2 = LCS(i,j-1)
		DPT[i,j] = max(ch1,ch2)
	return DPT[i,j]

ans = LCS(N,M)
```

---
Bottom-Up

```python
# input
s1 : str = 'string1'
s2 : str = 'string2'

# init  
N,M = len(s1), len(s2)
DPT : dict = dict()
# base cases
for i in range(N+1): DPT[i,0] = 0 # 1st col
for j in range(M+1): DPT[0,j] = 0 # 1st row

for i in range(1,N+1):
	for j in range(1,M+1):
		# choice dig.
		if s1[i] == s2[j]:
			DPT[i][j] = 1+DPT[i-1][j-1]
		else:
			ch1 = DPT[i-1,j]
			ch2 = DPT[i,j-1]
			DPT[i][j] = max(ch1, ch2)

ans = DPT[N][M]
```

----
Variations of **Longest Common Subsequence (LCS)** 

- Longest Common Substring : 
	- Q : Similar subsequence -> substring 
	- I/P : same (2 string) 
	- O/P : same (longest length)
	- Concept : 
		- **Substring** (continuous) v/s **Subsequence** (not continuous but in-order)
		- **Reset** length to 0 at every **discontinuity** -> `if s1[i] != s2[j] : DPT[i][j]=0` 
		- Answer : return the max value in DPT instead of the `DPT[M][N]`

- Printing Longest Common Subsequence :
	- Q : Same 
	- I/P Format : same (2 string) 
	- O/P Format : sequence instead of length 
	- Concept : 
		- LCS to create table + **backtrack** to generate string
		- Answer : Reverse string 

- Shortest Common Super-sequence :
	- Q : Super-sequence has both strings as subsequence 
	- I/P : same (2 string)
	- O/P : length 
	- Concept : 
		- Simple super-sequence will be S1+S2
		- Shortest ? **S1+ S2 - LCS(S1,S2)**
		- Answer = `len(S1)+ len(S2) - LCS(S1,S2)`

- Print Shortest Common Super-sequence :
	- Create a LCS
	- Backtrack appending every letter

- Longest Repeating Subsequence
	- Question : 
	- I/P : str
	- O/P :
	- Concept : 
		- `Mod_LCS(str, str)`
		- MOD = we only count those matches which have different index 
		  `s1[i] == s2[j] and i!=j`

```python 
if s1[i] == s2[j] and i!=j:
	DPT[i][j] = 1+DPT[i-1][j-1]
else:
	ch1 = DPT[i-1,j]
	ch2 = DPT[i,j-1]
	DPT[i][j] = max(ch1, ch2)
```

-  Sequence Pattern Matching
	- Question : If 1 string is a subsequence of the other 
	- I/P : S1, S2 
	- O/P : bool
	- Concept : 
		- LCS(S1,S2)
		- return `LCS(S1,S2) == min(S1,S2)`

- Minimum Insertion and Deletion to **convert String a to String b** (Not Edit)
	- Q : Different
	- I/P : same (2strings)
	- O/P : # insertion / deletion 
	- Concept : 
		- insertions/deletions = S - LCS(S1,S2)
		- insertions in one string and deletion in other 
		- answer = `len(S1) + len(S2) - 2*len(LCS(S1,S2))`

- Minimum **Edit Distance** : [link](https://www.youtube.com/watch?v=We3YDTzNXEk&ab_channel=TusharRoy-CodingMadeSimple)
	- Q : Similar to min insertion/deletion with +replacement
	- Concept :

```python 
# s2 is being converted to s1
if s1[i] == s2[j]:
	DPT[i][j] = DPT[i-1][j-1] # no operation 
else:
	ch1 = DPT[i-1,j] # s1[i] inserted/deleted   
	ch2 = DPT[i,j-1] # s2[j] deleted/inserted 
	ch3 = DPT[i-1,j-1] # replacement 
	DPT[i][j] = 1 + min(ch1, ch2, ch3)
```

- **Longest Palindromic Subsequence** (LPS)
	- Q : Subsequence
	- I/P : 1 string 
	- O/P : length 
	- Concept : 
		- answer = `LCS(S1,reverse(S1))`
		- length =  max value in DPT for substring

- Longest Palindromic **Substring**
	- Q : Subsequence or Substring
	- I/P : 1 string 
	- O/P : length or print 
	- Concept : 
		- LCS (S1,reverse(S1)) + **palindrome validation**
		- **validation** = palindrome from S and reverse(S) have the same original idx (in S) 
		- length = max valid value in DPT 
		- print = backtracking + validation 

```python 
S="abacdfgdcaba" 
S' = "abacdgfdcaba"
# max length of 4 for "abacd" 
# but longest common substring is "aba"
```

- Minimum number of insertion/deletion in a string to make it a **palindrome**
	- Q : Some what similar to LPS
	- I/P : 1 string
	- O/P : `int` 
	- Concept : 
		- `LPS(S) = LCS(S, reverse(S))`
		- `# deletion  = length(S) - LPS(S)`
		- **remember** : `# insertion = # deletion`


----

![[Pasted image 20231120180439.png]]

---