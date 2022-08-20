
# Invert Binary Tree


## Solution 1

```python
# Time O(N)/ Space O(N)
def invertBinaryTree(tree):
    queue = [tree]
    while len(queue):
        current = queue.pop()
        if current is None:
            continue
        swapleftright(current)
        queue.append(current.left)
        queue.append(current.right)
    
def swapleftright(subtree):
    subtree.left, subtree.right =  subtree.right, subtree.left

# This is the class of the input binary tree.
class BinaryTree:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None

```

## Solution 2

```python
# Time O(N)/ Space O(d) d is the depth of the tree
def invertBinaryTree(tree):
    if tree is None:
        return
    swapleftright(tree)
    invertBinaryTree(tree.left)
    invertBinaryTree(tree.right)

def swapleftright(tree):
    tree.left, tree.right = tree.right, tree.left


# This is the class of the input binary tree.
class BinaryTree:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None

```
