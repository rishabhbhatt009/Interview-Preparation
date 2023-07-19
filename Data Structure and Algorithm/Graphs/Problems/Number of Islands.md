# Number of Islands
![[Pasted image 20220621120926.png]]

## Explanation 
Traverse when you find 1 change it to 'X' as you go. 
Increment count of islands whenever you find 1

```python
def numIslands(self, grid: List[List[str]]) -> int:
	count = 0
	moves = [(1,0), (-1,0), (0,-1), (0,1)]
	check = lambda x,y : (x>=0 and x<len(grid)) and (y>=0 and y<len(grid[0]))
	
	def traverse (pos : tuple[int]) -> None :
		x,y = pos
		
		if grid[x][y] == '1':
			grid[x][y] = 'X'
			for move in moves:
				newx, newy = x+move[0], y+move[1]
				if check(newx, newy) :
					traverse((newx, newy))
	
	for i in range(len(grid)):
		for j in range(len(grid[0])):
			if grid[i][j] == '1':
				count += 1
				traverse((i,j))
				
	return count 
```

>[!Time and Space Complexity]+
>Time Complexity = $O(M*N)$
>Space Complexity= $O(M*N)$

## References 
1. Link to the question
2. [[BFS]] / [[DFS]]
