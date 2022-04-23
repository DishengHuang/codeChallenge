
# Task Assignment

You're given an integer k representing a number of workers and
an array of positive integers representing durations of tasks
that must be completed by the workers. Specifically, each worker
must complete two unique tasks and can work on one task at a time.
Workers will complete their assigned tasks in parallel, and the time
taken to complete all tasks will be equal to the time taken to complete
the longest pair of tasks (see the sample output for an explanation).

Write a function that returns the optimal assignment of tasks to each
worker such that the tasks are completed as fast as possible. 



### Sample Input 

```python
k = 3
tasks = [1,3,5,3,1,4]
```

### Sample Output 

```python
[
    [0, 2],
    [4, 5],
    [1, 3]
]
```

### Solution
Firstly, collect the index of the task time. Then, sort it and 
combine the shortest time with the longest time.  

```python
def taskAssignment(k, tasks):
	pairs = []
	task_index = getTaskDur(tasks)
	sort_tasks = sorted(tasks)
	
	for index in range(k):
		task1durIndex = task_index[sort_tasks[index]].pop()
		task2durIndex = task_index[sort_tasks[len(tasks) - 1 - index]].pop()
		pairs.append([task1durIndex, task2durIndex])
		
	return pairs
	
	
def getTaskDur(tasks):
	task_dict = {}
	index = 0
	for dur in tasks:
		if dur in task_dict:
			task_dict[dur].append(index)
		else:
			task_dict[dur] = [index]
		index += 1
	return task_dict
	
```