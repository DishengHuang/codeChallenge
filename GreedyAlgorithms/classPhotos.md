
# Class Photos

You're given two input arrays: one containing the heights of
all the students with red shirts and another one containing the
heights of all the students with blue shirts. These arrays will
always have the same length, and each height will be positive 
intger. Write a function that returns whether or not a class photos
that follows the stated guidelines can be taken.




### Sample Input
```python
redShirtHeights = [5,8,1,3,4]
blueShirtHeights = [6,9,2,4,5]
```

### Sample Output
```python
true
```

### Solution 1
Firstly, we sort both arrays into the descending order. 
Then, we compare both elements and check whether they are
strictly larger than one another.
```python
#Time O(nlog(n)) / Space O(1)
def classPhotos(redShirtHeights, blueShirtHeights):
	redShirtHeights.sort(reverse = True)
	blueShirtHeights.sort(reverse = True)
	
	firstRow = "red" if redShirtHeights[0] < blueShirtHeights[0] else "blue"
	
	for idx in range(len(redShirtHeights)):
		if firstRow == "red":
			if redShirtHeights[idx] >= blueShirtHeights[idx]:
				return False
		if firstRow == "blue":
			if redShirtHeights[idx] <= blueShirtHeights[idx]:
				return False
	return True
```

