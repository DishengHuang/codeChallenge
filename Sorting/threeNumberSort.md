
# Three Number Sort

You're given an array of integers and another array of three distinct
integers. The first array is guaranteed to only contain integers that
are in the second array, and the second array represents a desired order
for the first array. For example, a second array of [x,y,z] represents
a desired order of [x, x, ...,y,y,..,z,z] in the first array.

write a function that sorts the first array according to the desired
order in the second array.

The function should perform this in place, and it shouldnt use any
auxiliary space (it should only run with constant space: O(1) space).

Note that the desired order won't necessarily be ascending or descending and
that the first array won't necessarily contain all three integers found
in the second array -- it might only contain one or two.


## Sample Input

```python
array = [1,0,0,-1,-1,0,1,1]
order = [0,1,-1]
```

## Sample Output

```python
array = [0,0,0,1,1,1,-1,-1]
```


## Solution 1 (Bucket Sort)
Time O(N) / Space O(1)
```python
def threeNumberSort(array, order):
    # use the bucket to count the number of order elements
    order_bucket = [0, 0, 0]
    for element in array:
        bucket_index = order.index(element)
        order_bucket[bucket_index] += 1

    # rearrange the target array
    for i in range(3):
        value = order[i]
        num_count = order_bucket[i]

        order_before = sum(order_bucket[:i])
        for j in range(num_count):
            currentIndex = order_before + j
            array[currentIndex] = value

    return array

```

## Solution 2 (Sort the first value and the third value only)
Time O(N) / Space O(1)
```python
def threeNumberSort(array, order):
  firstValue = order[0]
	thirdValue = order[2]

	firstIndex = 0
	for index in range(len(array)):
		if array[index] == firstValue:
			array[firstIndex], array[index] = array[index], array[firstIndex]
			firstIndex += 1

	thirdIndex = len(array) - 1
	for index in reversed(range(len(array))):
		if array[index] == thirdValue:
			array[thirdIndex], array[index] = array[index], array[thirdIndex]
			thirdIndex -= 1

	return array
```


## Solution 3 (One loop to sort, the key is the secondIdx)
Time O(N) / Space O(1)
```python
def threeNumberSort(array, order):
  firstValue = order[0]
	secondValue = order[1]

  firstIdx, secondIdx, thirdIdx = 0, 0, len(array) - 1

  while secondIdx <= thirdIdx:
    value = array[secondIdx]

    if value == firstValue:
      array[firstIdx], array[secondIdx] = array[secondIdx], array[firstIdx]
      firstIdx += 1
      secondIdx += 1

    elif value == secondValue:
      secondIdx += 1

    else:
      array[thirdIdx], array[secondIdx] = array[secondIdx], array[thirdIdx]
      thirdIdx -= 1

  return array
```
