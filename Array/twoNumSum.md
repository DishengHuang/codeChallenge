
# Two Number Sum

Write a function that takes in a non-empty array of distinct integers and an integer representing a target sum.


### Sample Input

```python
array = [3,5,-4,8,11,1,-1,6]
targetSum = 10

```

### Sample Output

```python
[-1,11] 
```

### Solution 1
```python
# O(n) time | O(n) space
def twoNumberSum(array, targetSum):
    hashTable = {}
	for num1 in array:
		potentialPair = targetSum - num1
		if potentialPair in hashTable:
			return [potentialPair,num1]
		else:
			hashTable[num1] = True
	return []
 
```


### Solution 2
```python
# O(nlog(n)) time | O(1) space
def twoNumberSum(array, targetSum):
    array.sort()
	  left = 0
	  right = len(array) - 1
	  while left < right:
		    currentSum = array[left] + array[right]
		    if currentSum == targetSum:
			      return[array[left],array[right]]
		    elif currentSum < targetSum:
			      left += 1
		    elif currentSum > targetSum:
			      right -= 1
	  return []
 
```