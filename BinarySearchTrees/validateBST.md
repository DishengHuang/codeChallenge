
# Valid BST

Write a function that takes in a potentially invalid Binary
Search Tree (BST) and returns a boolean representing whether
the BST is valid.

### My thoughts
The solution to this problems is making good use of the property
of BST. The value of left nodes are smaller than the value on right 
nodes. If there exists some invalid values on the nodes, then this
may be not the valid BST.





## Solution

```python
# O(n) time | O(d) space
def validateBst(tree):
	return validateBSTtree(tree,-float("inf"),float("inf"))

def validateBSTtree(tree,minValue,maxValue):
	if tree is None:
		return True
	if tree.value < minValue or tree.value >= maxValue:
		return False
	isleftvalid = validateBSTtree(tree.left, minValue, tree.value)
	return isleftvalid and validateBSTtree(tree.right, tree.value, maxValue)
    
```

