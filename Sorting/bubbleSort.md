
# Bubble Sort

Write a function that takes in an array of integers and returns
a sorted version of that array. Use the Bubble Sort algorithm to
sort the array. 
### Sample Input

```python 
array = [8,5,2,9,5,6,3]
```

### Sample Output

```python 
[2,3,5,5,6,8,9]
```

## Solution

```python 
#Time O(n^2) | Space O(1)
def bubbleSort(array):
	isSorted = False
	counter = 0
	while not isSorted:
		isSorted = True
		for i in range(len(array) - 1 - counter):
			if array[i] > array[i + 1]:
				swap(i,i+1, array)
				isSorted = False
		counter += 1
	return array

def swap(currentIdx, nextIdx, array):
	array[currentIdx], array[nextIdx] = array[nextIdx], array[currentIdx] 
	
```