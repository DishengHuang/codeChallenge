
# Reconstruct BST

The pre-order traversal of a Binary Tree is a traversal technique
that starts at the tree's root node and visit nodes in the following
order:
(1) Current Node
(2) Left subtree
(3) Right subtree. Given a non-empty array of integers representing
the pre-order traversal of a Binary Search Tree (BST), write a
function that creates the relevant BST and returns its root node.
The input array will contain the value of BST nodes in the order in
which these nodes would be visited with a pre-order traversal.


### Sample Input

```python
preOrderTraversalValues = [10,4,2,1,5,17,19,18]
```

### Sample Output

```python
              10
             /  \
            4    17
          /  \    \
         2    5    19
        /         /
       1         18
```
### Solution 1
```python
# Time O(n^2) | Space O(n) --- where n is the length of the input array
class BST:
    def __init__(self, value, left=None, right=None):
        self.value = value
        self.left = left
        self.right = right


def reconstructBst(preOrderTraversalValues):

    #if there exists empty array
	if len(preOrderTraversalValues) == 0:
		return None

    #current node value
	currentValue = preOrderTraversalValues[0]
	rightSubtreeRootIdx = len(preOrderTraversalValues)

    #find the right Subtree root idx by finding the
    #idx of the value greater than current value
	for idx in range(1, len(preOrderTraversalValues)):
		value = preOrderTraversalValues[idx]
		if value >= currentValue:
			rightSubtreeRootIdx = idx
			break
	#rescursive to build the subtree
	leftsubtree = reconstructBst(preOrderTraversalValues[1:rightSubtreeRootIdx])
	rightsubtree = reconstructBst(preOrderTraversalValues[rightSubtreeRootIdx:])

    #return the trees
	return BST(currentValue, leftsubtree, rightsubtree)

```


### Solution 2
```python
# Time O(n) | Space O(n)
class BST:
    def __init__(self, value, left=None, right=None):
        self.value = value
        self.left = left
        self.right = right

class TreeInfo:
	def __init__(self, rootIdx):
		self.rootIdx = rootIdx


def reconstructBst(preOrderTraversalValues):
    treeInfo = TreeInfo(0)
    return reconstructBstFromRange(float("-inf"),float("inf"),preOrderTraversalValues,treeInfo)

def reconstructBstFromRange(lowerBound, upperBound, preOrderTraversalValues, currentSubtreeInfo):
	if currentSubtreeInfo.rootIdx == len(preOrderTraversalValues):
		return None

	rootValue = preOrderTraversalValues[currentSubtreeInfo.rootIdx]
	if rootValue < lowerBound or rootValue >= upperBound:
		return None

	currentSubtreeInfo.rootIdx += 1
	leftSubtree = reconstructBstFromRange(lowerBound, rootValue, preOrderTraversalValues, currentSubtreeInfo)
	rightSubtree = reconstructBstFromRange(rootValue, upperBound, preOrderTraversalValues, currentSubtreeInfo)

	return BST(rootValue, leftSubtree, rightSubtree)
```
