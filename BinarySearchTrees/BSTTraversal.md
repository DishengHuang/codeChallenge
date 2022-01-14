
# BST Traversal

Write three functions that takes in a Binary Search Tree (BST) and
an empty array, traverse the BST, add its nodes'values to the input
array, and return that array. The three functions should traverse 
the BST using the in-order, pre-order, and post-order tree-traversal
techniques, respectively.

## Sample Input
```python
tree =    10
         /  \
        5   15
       / \    \
      2  5    22
     /
    1
array = []
```
## Sample Output
```python
inOrderTraverse = [1,2,5,5,10,15,22]
preOrderTraverse = [10,5,2,1,5,15,22]
postOrderTraverse = [1,2,5,5,22,15,10]
```
## Solution
```python
#Time O(n)/ Space O(n)
def inOrderTraverse(tree, array):
    if tree is not None:
		inOrderTraverse(tree.left,array)
		array.append(tree.value)
		inOrderTraverse(tree.right,array)
	return array

#Time O(n)/ Space O(n)
def preOrderTraverse(tree, array):
    if tree is not None:
		array.append(tree.value)
		preOrderTraverse(tree.left,array)
		preOrderTraverse(tree.right,array)
	return array

#Time O(n)/ Space O(n)
def postOrderTraverse(tree, array):
    if tree is not None:
		postOrderTraverse(tree.left,array)
		postOrderTraverse(tree.right,array)
		array.append(tree.value)
	return array
```

