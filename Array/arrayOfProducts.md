
# Array Of Product

Write a function that takes in a non-empty array of integers
and returns an array of the same length, where each element
in the array is equal to the product of every other number
in the input array.

### Sample Input

```python
array = [5,1,4,2]
```

### Sample Output

```python
[8,40,10,20]
```
### Solution 1 (Brute Force Approach)
```python
#Time O(n^2) and Space O(n)
def arrayOfProducts(array):
	products = []
    for i in range(len(array)):
		currentProduct = 1
		for j in range(len(array)):
			if i == j:
				continue
			else:
				currentProduct = currentProduct * array[j]
		products.append(currentProduct)
	return products
```

### Solution 2 (Create the Left and Right Array, and Multiply them)
```python
#Time O(n) and Space O(n)
def arrayOfProducts(array):
	products = [1 for _ in range(len(array))]
	left = [1 for _ in range(len(array))]
	right = [1 for _ in range(len(array))]

    left_product = 1
    for i in range(len(array)):
        left[i] = left_product
        left_product *= array[i]

    right_product = 1
    for i in reversed(range(len(array))):
        right[i] = right_product
        right_product *= array[i]

    for i in range(len(array)):
        products[i] = left[i] * right[i]
    return products

```

### Solution 3 (Create One Array and Multiply Existing Elements)
```python
#Time O(n) and Space O(n)
def arrayOfProducts(array):
    products = [1 for _ in range(len(array))]

    left_product = 1
    for i in range(len(array)):
        products[i] = left_product
        left_product *= array[i]

    right_product = 1
    for i in reversed(range(len(array))):
        products[i] *= right_product
        right_product *= array[i]

    return products

```
