
# Permutations

Write a function that takes in an array of unique integers and returns an array of all permutations of those integers
in no particular order.

if the input array is empty, the function should return an empty array.


### Solution 1

```python
def getPermutations(array):
	permutations = []
	permutationHelper(array, [], permutations)
	return permutations

def permutationHelper(array, currentPermutation, permutations):
	if not len(array) and len(currentPermutation):
		permutations.append(currentPermutation)
	else:
		for i in range(len(array)):
			newArray = array[:i] + array[i+1:]
			newPermutation = currentPermutation + [array[i]]
			permutationHelper(newArray,newPermutation,permutations)
```


### Solution 2

```python
def getPermutations(array):
    permutations = []
	permutationHelper(0, array, permutations)
	return permutations

def permutationHelper(i, array, permutations):
	if i == len(array) - 1:
		return permutations.append(array[:])
	else:
		for j in range(i, len(array)):
			swap(i, j, array)
			permutationHelper(i + 1, array, permutations)
			swap(i, j, array)

def swap(i, j, array):
	array[i], array[j] = array[j], array[i]

```
