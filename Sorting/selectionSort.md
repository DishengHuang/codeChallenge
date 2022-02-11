
# Selection Sort

Write a function that takes in an array of integers and returns
a sorted version of that array. Use the Selection Sort algorithm to
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
def selectionSort(array):
    currentIndex = 0
	while currentIndex < len(array) - 1:
		smallestIndex = currentIndex
		for i in range(currentIndex + 1, len(array)):
			if array[smallestIndex] > array[i]:
				smallestIndex = i
		swap(currentIndex,smallestIndex,array)
		currentIndex += 1
	return array

def swap(i, j, array):
	array[i], array[j] = array[j], array[i]
```