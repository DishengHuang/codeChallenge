
# Smallest Difference



## Solution 1

```python
def smallestDifference(arrayOne, arrayTwo):
    # Write your code here.
    smallest_diff = float("inf")
	for i in arrayOne:
		for j in arrayTwo:
			if abs(i - j) < smallest_diff:
				smallest_array = [i,j]
				smallest_diff = abs(i - j) 
	return smallest_array
```

