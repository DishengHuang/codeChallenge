
# Merge Overlapping Intervals

Write a function that takes in a non-empty array of arbitrary
intervals, merges any overlapping intervals, and returns the
new intervals in no particular order.




### Sample Input

```python
intervals = [[1,2],[3,5],[4,7],[6,8],[9,10]]
```
### Sample Output

```python
[[1,2],[3,8],[9,10]]
```

## My Thoughts
Firstly, we may need to sort the intervals by the starting values.
We may then check whether the adjacent arrays is overlapped or not.
If they are overlapped, we may merge and store it into the output
array. 

### Solution 
```python
def mergeOverlappingIntervals(intervals):
	# sort the intervals by the first value
    sorted_array = sorted(intervals, key = lambda x:x[0])	
	# create the output array
	output_array = []
	# current interval
	current_interval = sorted_array[0]
	output_array.append(current_interval)
	
	# iteration
	for next_interval in sorted_array:
		_, current_end = current_interval
		next_start, next_end = next_interval
		
		if current_end >= next_start:
			current_interval[1] = max(current_end,next_end)
		else:
			current_interval = next_interval
			output_array.append(current_interval)
	
    return output_array
```

