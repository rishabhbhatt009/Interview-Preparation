# Valid Tree
![[Pasted image 20220617003649.png]] 

## Explanation 
Properties of a Valid Tree :
	1. A valid tree does not have a cycle, which means there exist only one path between 2 connected nodes.
	2. It has only one root node. 

We can create a [[Disjoint Set]] data structure. 
1. In the union() if the roots of 2 nodes are same before they are connected through union => that there is an already existing path b/w the nodes. Therefore we can infer it is not a valid tree. 
2. *Edge case* : At the end of all unions there should be only one common root node. 

```python
# Write solution

```

>[!Time and Space Complexity]-
>Discuss the time and space complexity 

## References 
1. [Link to the question](https://leetcode.com/explore/featured/card/graph/618/disjoint-set/3910/) 
2. [[Disjoint Set]]
3. TAGS : #Leetcode