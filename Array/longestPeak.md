
# Longest Peak

Write a function that takes in an array of integers and returns 
the longest peak in the array.




### Sample Input

```python
array = [1,2,3,3,4,0,10,6,5,-1,-3,2,3]
```
### Sample Output

```python
6 # 0,10,6,5,-1,-3
```

### My Thoughts
This question can be divided into two parts. Firstly, we could find
all the peaks in the array and then compare their lengths and find
the longest one. How to find the peaks? We compare the current value 
with its adjacent values. How to find the lengths? We could start
from the peak and see how far out to the left and how far out to the
right.

### Solution

```python
def longestPeak(array):
    # Write your code here.
    longestPeakLength = 0
	i = 1
	# avoid the edge cases
	while i < len(array) - 1:
		#find the peaks by checking the adjacent values
		isPeak = array[i-1] < array[i] and array[i] > array[i+1] 
		if not isPeak:
			i += 1
			continue		
		#check the peak length
		leftIndex = i - 2
		while leftIndex >= 0 and array[leftIndex] < array[leftIndex + 1]:
			leftIndex -= 1
			
		rightIndex = i + 2
		while rightIndex < len(array) and array[rightIndex] < array[rightIndex - 1]:
			rightIndex += 1
		
		currentPeakLength = rightIndex - leftIndex - 1
		longestPeakLength = max(longestPeakLength,currentPeakLength)
		i = rightIndex
		
	return longestPeakLength
		
```


