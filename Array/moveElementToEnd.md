
# Move Element To End
Given an array of integers and an integer. Write a function that moves all instances of that integer in the array to the end of the array and returns the array.
The function should perform this in place(i.e., it should mutate the input array) and doesn't need to maintain the order of the other integers.





### Sample Input

```python
array = [2,1,2,2,2,3,4,2]
toMove = 2
```

### Sample Output
```python
[1,3,4,2,2,2,2,2]
```

### Solution 1
```python
#Time O(N) and Space O(N)
def moveElementToEnd(array, toMove):
    first = []
	second = []
	for n in array:
		if n == toMove:
			second.append(n)
		else:
			first.append(n)
	return first + second
```
### Solution 2
```python
#Time O(N) and Space O(1)
def moveElementToEnd(array, toMove):
    left = 0
	right = len(array) - 1
	while left < right:
		while left < right and array[right] == toMove:
			right -= 1
		if array[left] == toMove:
			array[left], array[right] = array[right], array[left]
		left += 1
	return array   
```