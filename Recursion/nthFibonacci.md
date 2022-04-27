
# Nth Fibonacii

The Fibonacii sequence is defined as follows: the first number
of the sequence is 0, the second number is 1, and the nth number
is the sum of the (n - 1)th and (n -2)th numbers. Write a function
that takes in an integer n and returns the nth Fibonacii number.



### Solution 1
This is the navie method. Firstly, define the two base cases and
then use the recursion 

```python
def getNthFib(n):
	# Time O(n^2) / Space O(n)
    if n == 1:
		return 0
	elif n == 2:
		return 1
	else:
		return getNthFib(n-1) + getNthFib(n-2)
```

### Solution 2
This solution is a little bit optimal than the solution 1. This is
because we introduce the hash table to reduce the depulicated 
computation.

```python
def getNthFib(n, memorize = {1: 0, 2: 1}):
    #Time O(n)/ Space O(n)
	if n in memorize:
		return memorize[n]
	else:
		memorize[n] = getNthFib(n - 1, memorize) + getNthFib(n - 2, memorize)
		return memorize[n]
```

### Solution 3
We only store the last two numbers and sum those two
numbers. 

```python
def getNthFib(n):
	sum_list = [0, 1]
	counter = 3
	while counter <= n:
		f_sum = sum_list[0] + sum_list[1]
		sum_list[0] = sum_list[1]
		sum_list[1] = f_sum
		counter += 1
	return 0 if n == 1  else sum_list[1]
```

