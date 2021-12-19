
# Spiral Traverse

Write a function that takes in an n x m two-dimensional array (that
can be squared-shaped when n == m) and returns a one-dimensional array
of all the array's elements in spiral order.




### Sample Input

```python
array = [
    [1,2,3,4],
    [12,13,14,5],
    [11,16,15,6],
    [10,9,8,7],
]
```


### Sample Output

```python
[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16]
```
### My thoughts about this questions

The key of this questions is how to identify the index of the sample input and 
append those elements into the result array. This means we need to identify 
the exact row number and col number each time and append into the result list.

### Solution 1 (Iterative)
```python
#Time O(n) and Space O(n)
def spiralTraverse(array):
    # Write your code here.
    result = []
	startRow, endRow = 0, len(array) - 1
	startCol, endCol = 0, len(array[0]) - 1
	
	while startRow <= endRow and startCol <= endCol:
		#left to right
		for col in range(startCol,endCol + 1):
			result.append(array[startRow][col])
		#first row to end row
		for row in range(startRow + 1,endRow + 1):
			result.append(array[row][endCol])
		#right to left
		for col in reversed(range(startCol,endCol)):
			if startRow == endRow:
				break
			result.append(array[endRow][col])
		#last row to first row
		for row in reversed(range(startRow + 1,endRow)):
			if startCol == endCol:
				break
			result.append(array[row][startCol])
		
		startRow += 1
		endRow -= 1
		startCol += 1
		endCol -= 1
	
	return result
```

### Solution 2 (Resursive)
```python
#Same logic as solution 1
#Time O(n) and Space O(n)
def spiralTraverse(array):
    # Write your code here.
    result = []
	spiralFill(array, 0, len(array) - 1, 0 , len(array[0]) - 1, result)
	return result

def spiralFill(array, startRow, endRow, startCol, endCol, result):
	#when to stop
	if startRow > endRow or startCol > endCol:
		return
	for col in range(startCol, endCol + 1):
		result.append(array[startRow][col])
	for row in range(startRow + 1, endRow + 1):
		result.append(array[row][endCol])
	for col in reversed(range(startCol,endCol)):
		if startRow == endRow:
			break
		result.append(array[endRow][col])
	for row in reversed(range(startRow + 1,endRow)):
		if startCol == endCol:
			break
		result.append(array[row][startCol])
	
	spiralFill(array, startRow + 1, endRow - 1, startCol + 1, endCol - 1, result)
		

```