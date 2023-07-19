### Binary Search


Core Algorithm

```python
def search (array:list[int], value:int) -> int :
	"""
	Binary Search Algorithm 
	"""
	start, end = 0, len(array) - 1
	while start <= end :
		mid = (start + end) // 2
		if array[mid] == value :
			return mid
		elif (array[mid] < value) :
			start = mid+1
		else :
			end = mid-1
	return -1 
```

Time Complexity : $O(log(N))$ 

Types :
- Simple no array (sqrt)
- API call
- Rotated