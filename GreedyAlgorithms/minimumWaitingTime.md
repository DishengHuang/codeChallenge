
# Minimum Waiting Time

You've given a non-empty array of positive integers representing
the amounts of time that specific queries take to execute.
Only one query can be executed at a time, but the queries can be
executed in any order.



### Sample Input

```python
queries = [3,2,1,2,6]
```

### Sample Output

```python
17
```

### Solution 1
Firstly, sort the array and then compute the current waiting time
and add to the total waiting time.
```python
def minimumWaitingTime(queries):
	queries.sort()
	current_wait = 0
	total_wait = 0
	for index in range(len(queries) - 1):
		current_wait += queries[index]
		total_wait = total_wait + current_wait

    return total_wait
```


### Solution 2
```python
#Time O(n)/ Space O(1)
def minimumWaitingTime(queries):
	queries.sort()
    totalWait = 0
	for idx, value in enumerate(queries):
		queriesLeft = len(queries) - (idx + 1)
		totalWait += value*queriesLeft
	return totalWait
```
