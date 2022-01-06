
# BST Construction

Write a BST class for a Binary Search Tree. The class should support:
(a) Inserting values with the insert method (b) Removing values
with the remove method; this method should only remove the first
instance of a given value. (c) Searching for values with the contains
method.

### Samples

```python
#Sample BST
      10
     /  \
    5   15
   / \   / \
  2  5  13  22
 /       \
1        14

# case 1
insert(12):
      10
     /  \
    5   15
   / \   / \
  2  5  13  22
 /      / \
1      12 14

# case 2
remove(10):
      12
     /  \
    5   15
   / \  / \
  2  5 13  22
 /       \
1        14

# case 3
contain(15): true
```
### My thoughts
The key to solve this questions are as follows. Basically,
inserting the node and searching the node share the similar
logic. According to the property of BST, we could
compare each node and select the subtree to insert
or remove the nodes. The difficulty of the remove node is that
you have to consider different edges case. To be specific,
(1) The node you remove has both left and right subtree
(2) The node you remove is root node and has only left or right subtree or none.
(3) The node you remove has only left or right subtree.


```python
class BST:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None
    # Avg O(log(n)) time / O(1) space
    # Worst O(n) time / O(1) space
    def insert(self, value):
        currentNode = self
		while True:
			if value < currentNode.value:
				if currentNode.left is None:
					currentNode.left = BST(value)
					break
				else:
					currentNode = currentNode.left
			else:
				if currentNode.right is None:
					currentNode.right = BST(value)
					break
				else:
					currentNode = currentNode.right
        return self
    # Avg O(log(n)) time / O(1) space
    # Worst O(n) time / O(1) space
    def contains(self, value):
        currentNode = self
		while currentNode is not None:
			if value < currentNode.value:
				currentNode = currentNode.left
			elif value > currentNode.value:
				currentNode = currentNode.right
			else:
				return True
		return False
    # Avg O(log(n)) time / O(1) space
    # Worst O(n) time / O(1) space				
    def remove(self, value, parentNode = None):
		currentNode = self
		while currentNode is not None:
			if value < currentNode.value:
				parentNode = currentNode
				currentNode = currentNode.left
			elif value > currentNode.value:
				parentNode = currentNode
				currentNode = currentNode.right
			else:
				if currentNode.left is not None and currentNode.right is not None:
					currentNode.value = currentNode.right.getMinValue()
					currentNode.right.remove(currentNode.value,currentNode)
				elif parentNode is None:
					if currentNode.left is not None:
						currentNode.value = currentNode.left.value
						currentNode.right = currentNode.left.right
						currentNode.left = currentNode.left.left
					elif currentNode.right is not None:
						currentNode.value = currentNode.right.value
						currentNode.left = currentNode.right.left
						currentNode.right = currentNode.right.right
					else:
						pass
				elif parentNode.left == currentNode:
					parentNode.left = currentNode.left if currentNode.left is not None else currentNode.right
				elif parentNode.right == currentNode:
					parentNode.right = currentNode.left if currentNode.left is not None else currentNode.right
				break
        return self

	def getMinValue(self):
		currentNode = self
		while currentNode.left is not None:
			currentNode = currentNode.left
		return currentNode.value

```
