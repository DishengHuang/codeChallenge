
# Validate Subsequence

Given two non-empty arrays of integers, write a function that determines whether the second array is a subsequence of the first one.




### Sample Input

```python
array = [5,1,22,25,6,-1,8,10]
sequence = [1,6,-1,10]
```

### Sample Output

```python
true
```
### Solution 1

```python
#O(n) Time / O(1) Space
def isValidSubsequence(array, sequence):
    # Write your code here.
    arrIndex = 0
	seqIndex = 0
	while arrIndex < len(array)  and seqIndex < len(sequence):
		if seqIndex == len(sequence):
			break
		if array[arrIndex] == sequence[seqIndex]:
			seqIndex += 1
		arrIndex += 1
	return seqIndex == len(sequence) 
```

### Solution 2

```python
#O(n) Time / O(1) Space
def isValidSubsequence(array, sequence):
    # Write your code here.
	seqIndex = 0
	for num in array:
		if seqIndex == len(sequence):
			break
		if num == sequence[seqIndex]:
			seqIndex += 1
	return seqIndex == len(sequence)
```