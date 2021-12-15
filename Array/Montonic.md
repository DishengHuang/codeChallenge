
# Monotonic Array

Write a function that takes in an array of integers and returns a boolean representing whether the array is monotonic.





### Sample Input

```python
array = [-1,-5,-10,-1100,-1100,-1101,-1102,-9001]
```

### Sample Output

```python
true
```

## My thought for solution 1
Checking the direction of an array is very important. The direction of
an array could be flat, upwards, and downwards. The key for this question
is to keep checking whether the array breaks the original direction. Below 
is the coding solution for this problem.
```python
#Time O(N), Space O(1)

def isMonotonic(array):
    if len(array) <= 2 :
		return True
	
	# direction 
	direction = array[1] - array[0]
	# loop the array
	for i in range(2, len(array)):
		# if the direction is flat, then we need to keep searching
		if direction == 0:
			direction = array[i] - array[i-1]
			continue
        # check if the direction has been broken
		if directionBreak(direction,array[i-1],array[i]):
			return False
	return True

def directionBreak(direction, preNum, curNum):
	if direction < 0:
		return (curNum - preNum) > 0
	return (curNum - preNum) < 0
```

## My thought for solution 2
Solution 1 seems a little bit complicated. In fact, we could use 
a more simpler way to solve this problem. We could just
check whether the array is nondecreasing or nonincreasing. If yes,
this array should be monotonic. If not, this array should
not be the monotonic.

```python
def isMonotonic(array):
    # Write your code here.
    isNonDecrease = True
	isNonIncrease = True
	for i in range(1,len(array)):
		diff = array[i] - array[i-1]
		if diff < 0:
			isNonDecrease = False
		elif diff > 0:
			isNonIncrease = False
	return isNonDecrease or isNonIncrease
	
```