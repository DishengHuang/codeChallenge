
# Tandem Bicycle

A tandem bicycle is a bicycle that's operated by two people:
person A and person B. Both people pedal the bicycle, but the
person that pedals faster dictates the speed of the bicycle. So
if person A pedals at a speed of 5, and person B pedals at a speed
of 4, the tandem bicycle moves at a speed of 5 (i.e., tandemSpeed = 
max(speedA, speedB)).

Write a function that returns the maximum possible total speed or the
minimum possible total speed of all of the tandem bicycle being ridden
based on an input parameter, fastest. If fastest = true, your function
should return the maximum possible total speed; otherwise it should return
the minimum total speed.

### Sample Input

```python
redShirtSpeeds = [5, 5, 3, 9, 2]
blueShirtSpeeds = [3, 6, 7, 2, 1]
fastest = true
```

### Sample Output

```python
32
```

### Solution

```python
def tandemBicycle(redShirtSpeeds, blueShirtSpeeds, fastest):
    #Time O(nlog(n))/ Space O(1)
	redShirtSpeeds.sort()
	blueShirtSpeeds.sort()
	
	if not fastest:
		arrangeArray(redShirtSpeeds)
		
	total_speed = 0
	for index in range(len(redShirtSpeeds)):
		ride_1 = redShirtSpeeds[index]
		ride_2 = blueShirtSpeeds[len(redShirtSpeeds) - index - 1]
		speed = max(ride_1, ride_2)
		total_speed += speed
		
	return total_speed
		
def arrangeArray(array):
	start = 0
	end = len(array) - 1
	while start < end:
		array[start], array[end] = array[end], array[start]
		start += 1
		end -= 1
```