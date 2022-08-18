
# Branch Sums

Write a function that takes in a Binary Tree and returns a list of
its branch sums ordered from leftmost branch sum to rightmost
branch sum. 

A branch sum is the sum of all values in a Binary Tree branch. A 
Binary Tree branch is a path of nodes in a tree that starts at the
root node and ends at any leaf node.

Each BinaryTree node has an integer value, a left child node, and
a right child node. Children nodes can either be BinaryTree nodes
themselves or None/null. 


## Solution 1

```python
#Time O(N)/ Space O(N)
# This is the class of the input root. Do not edit it.
class BinaryTree:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None


def branchSums(root):
    sums = []
    calculateSum(root, 0, sums)
    return sums

def calculateSum(node, runningSum, sums):
    if node is None:
        return
    runningSum = node.value + runningSum
    if node.left is None and node.right is None:
        sums.append(runningSum)
        return
    calculateSum(node.left, runningSum, sums)
    calculateSum(node.right, runningSum, sums)
     
```
## Solution for LC 112 (Path Sum)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        sums = []
        calculateSum(root, 0, sums, targetSum)
        return True if targetSum in sums else False
    
def calculateSum(node, runningSum, sums, target):
    if node is None:
        return
    runningSum = runningSum + node.val
    if node.left is None and node.right is None:
        sums.append(runningSum)
        if runningSum == target:
            return
    
    calculateSum(node.left, runningSum,sums, target)
    calculateSum(node.right,runningSum,sums, target)
     
```


