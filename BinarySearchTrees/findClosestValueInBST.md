
# Find Closest Value In BST

Write a function that takes in BST and a target integer value and 
returns the cloest value to that target value contained in the BST.




### Solution 1 (Recursively)

```python 
# Avg Time O(log(n)) / Space O(log(n))
# Worst Time O(n) / Space O(n)
def findClosestValueInBst(tree, target):
    return ClosestValueInBST(tree, target, float("inf"))

def ClosestValueInBST(tree, target, closest):
	# base case
	if tree is None: 
		return closest
	# compute the distance between the nodes and target
	if abs(tree.value - target) < abs(closest - target):
		closest = tree.value
	# use BST property to determine the direction of the tree search
	if tree.value < target:
		return ClosestValueInBST(tree.right, target, closest)
	elif tree.value > target:
		return ClosestValueInBST(tree.left, target, closest)
	else:
		return closest

# This is the class of the input tree.
class BST:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None
```

### Solution 2 (Iterative)

```python 
# Avg Time O(log(n)) / Space O(1)
# Worst Time O(n) / Space O(1)
def findClosestValueInBst(tree, target):
	currentNone = tree	
	closest = float("inf")
	while currentNone is not None:
		# compute the distance between the nodes and target
		if abs(currentNone.value - target) < abs(closest - target):
			closest = currentNone.value
		# use BST property to determine the direction of the tree search
		if currentNone.value < target:
			currentNone = currentNone.right
		elif currentNone.value > target:
			currentNone = currentNone.left
		else:
			break
	return closest

# This is the class of the input tree.
class BST:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None


```
