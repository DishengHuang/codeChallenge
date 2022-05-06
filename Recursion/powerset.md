
# Powerset

Write a function that takes in an array of unique integers and returns its powerset.
The powerset P(X) of a set X is the set of all subsets of X. For example,
the powerset of [1,2] is [[],[1],[2],[1,2]]. Note that the sets in the
powerset do not need to be in any particular order.

### Sample Input

```python
array = [1,2,3]
```

### Sample Output

```python
[[],[1],[2],[3],[1,2],[1,3],[2,3],[1,2,3]]
```

### Solution 1
This is using the iteration method
```python
### Time O(n*2^n)/ Space O(n*2^n)
def powerset(array):
	#Initial cases
	subsets = [[]]
	#Check the current element
	for ele in array:
	#Add the current element into the subsets
		for s in range(len(subsets)):
			currentSubset = subsets[s] + [ele]
			subsets.append(currentSubset)
	return subsets
```

### Solution 2
This is using the recursion method
```python
### Time O(n*2^n)/ Space O(n*2^n)
def powerset(array, idx = None):
    if idx is None:
			idx = len(array) - 1
		if idx < 0:
			return [[]]
		ele = array[idx]
		subsets = powerset(array, idx - 1)
		for s in range(len(subsets)):
			currentSubset = subsets[s] + [ele]
			subsets.append(currentSubset)
		return subsets
```
