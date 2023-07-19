# The Earliest Moment When Everyone Become Friends
![[Pasted image 20220617113119.png]]

## Explanation 
Use a [[Disjoint Set]] data structure. 
1. sort the logs in ascending order of time 
2. keep connecting nodes + tracking the number of root nodes (==remember== -> `nonlocal`) as you go through the logs
3. if number of root nodes reaches 1 return time else return -1

```python
# Write solution

```

![[Disjoint Set#^57dd16]]

>[!Time and Space Complexity]+
>Discuss the time and space complexity 

## References 
1. Link to the question
2. [[Disjoint Set]]
3. TAGS : #Leetcode