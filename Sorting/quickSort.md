
# Quick Sort

Write a function that takes in an array of integers and returns a sorted verison of that array. Use the Quick Sort algorithm to sort the array.





## Sample Input

```python
array = [8,5,2,9,6,3]
```

## Sample Output

```python
[2,3,5,5,6,8,9]
```

## Solution
The key to this solution is to find the pivot value and compare it, 
and sort the small subarray. 

```python
def quickSort(array):
    # recurive helper function
	quickSortHelper(array, 0, len(array) - 1)
	return array

def quickSortHelper(array, startIdx, endIdx):
	# case to return
	if startIdx >= endIdx:
		return
	pivotIdx = startIdx
	leftIdx = startIdx + 1
	rightIdx = endIdx
	# sort the array
	while leftIdx <= rightIdx:
		if array[leftIdx] > array[pivotIdx] and array[rightIdx] < array[pivotIdx]:
			swap(array, leftIdx, rightIdx)
		if array[leftIdx] <= array[pivotIdx]:
			leftIdx += 1
		if array[rightIdx] >= array[pivotIdx]:
			rightIdx -= 1
	swap(array, pivotIdx, rightIdx)
	# find the small subarray and do the swap on the small array first (rightIdx is pivotIdx)
	leftArrayIsSmall = rightIdx - 1 - startIdx < endIdx - (rightIdx + 1)
	if leftArrayIsSmall:
		quickSortHelper(array, startIdx, rightIdx - 1)
		quickSortHelper(array, rightIdx + 1, endIdx)
	else:
		quickSortHelper(array, rightIdx + 1, endIdx)
		quickSortHelper(array, startIdx, rightIdx - 1)
		
def swap(array, i, j):
	array[i], array[j] = array[j], array[i]
```