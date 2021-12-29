
# First Duplicate Value

Given an array of integers between 1 and n, inclusive, where n is 
the length of the array, write a function that returns the first integer
that appears more than once (when the array is read from left 
to right).


### Sample Input 1
```python
array = [2,1,5,2,3,3,4]
```
### Sample Output 1
```python
2
```
### Sample Input 2
```python
array = [2,1,5,3,3,2,4]
```
### Sample Output 2
```python
3
```

## My thoughts
The key for this problem is about how to check whether the value 
is duplicated or not.

### Solution 1 (Brute Force Approach)
```python
#Time O(n^2) and Space O(1)
def firstDuplicateValue(array):
	minimumIndex = len(array)
	for i in range(len(array)):
		num = array[i]
		for j in range(i + 1, len(array)):
			if num == array[j]:
				minimumIndex = min(minimumIndex,j)
    return -1 if minimumIndex == len(array) else array[minimumIndex]
```


### Solution 2 
```python
#Time O(n) and Space O(n)
def firstDuplicateValue(array):
    check_duplicate = set()
	for e in array:
		if e not in check_duplicate:
			check_duplicate.add(e)
		else:
			return e
    return -1
```

### Solution 3
We could use each index to represent if we have found the value
that maps to this index already, and then as soon as we find that
value again, it's gonna map to the same index, we see this index 
or the value of this index is negative. We found the first duplicated
value and return this value.  
```python
#Time O(n) and Space O(1)
def firstDuplicateValue(array):
	for i in range(len(array)):
		index = abs(array[i]) - 1
		if array[index] < 0:
			return abs(array[i])
		else:
			array[index] *= -1
	return -1
```

