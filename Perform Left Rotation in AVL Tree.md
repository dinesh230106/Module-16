# Ex. No: 16E - Perform Left Rotation in AVL Tree and Insert '7'

## AIM:
To write a Python function `def leftRotate(self, z):` to perform the left rotation operation in an AVL Tree and insert the element '7' into it.

---

## ALGORITHM:

### Step 1: Start the program.

### Step 2: Define the `TreeNode` class to represent each node in the AVL Tree:
- Key value
- Left and right child pointers
- Height of the node

### Step 3: Define the `AVL_Tree` class to manage AVL operations.

### Step 4: In the `insert()` method:
- Insert the key using standard Binary Search Tree logic.
- Update the height of the current node.
- Calculate the balance factor to detect imbalance.
- Based on balance factor and key position, perform necessary rotations.

### Step 5: Define `leftRotate(z)` method:
- Let `y = z.right` and `T2 = y.left`
- Make `z` the left child of `y`
- Assign `T2` as the right child of `z`
- Update heights of `z` and `y`
- Return `y` as the new root of the subtree

### Step 6: Insert the key `'7'` using the `insert()` method. If it causes imbalance, perform appropriate rotation.

### Step 7: Display the tree using `preOrder()` traversal to show the structure after insertion and rotation.

### Step 8: End the program.

---

## PYTHON PROGRAM

```
# Reg.No: 212223060057
# Name: DINESH KUMAR A
# Ex.No: 16E - Left Rotation in AVL Tree and Insert '7'

class TreeNode:
    def __init__(self, key):
        self.key = key
        self.left = None
        self.right = None
        self.height = 1

class AVL_Tree:
    def insert(self, root, key):
        # Standard BST insertion
        if not root:
            return TreeNode(key)
        elif key < root.key:
            root.left = self.insert(root.left, key)
        else:
            root.right = self.insert(root.right, key)
        
        # Update height
        root.height = 1 + max(self.getHeight(root.left), self.getHeight(root.right))
        
        # Get balance factor
        balance = self.getBalance(root)
        
        # Left Left Case
        if balance > 1 and key < root.left.key:
            return self.rightRotate(root)
        # Right Right Case
        if balance < -1 and key > root.right.key:
            return self.leftRotate(root)
        # Left Right Case
        if balance > 1 and key > root.left.key:
            root.left = self.leftRotate(root.left)
            return self.rightRotate(root)
        # Right Left Case
        if balance < -1 and key < root.right.key:
            root.right = self.rightRotate(root.right)
            return self.leftRotate(root)
        
        return root

    def leftRotate(self, z):
        y = z.right
        T2 = y.left
        y.left = z
        z.right = T2
        z.height = 1 + max(self.getHeight(z.left), self.getHeight(z.right))
        y.height = 1 + max(self.getHeight(y.left), self.getHeight(y.right))
        return y

    def rightRotate(self, z):
        y = z.left
        T3 = y.right
        y.right = z
        z.left = T3
        z.height = 1 + max(self.getHeight(z.left), self.getHeight(z.right))
        y.height = 1 + max(self.getHeight(y.left), self.getHeight(y.right))
        return y

    def getHeight(self, node):
        if not node:
            return 0
        return node.height

    def getBalance(self, node):
        if not node:
            return 0
        return self.getHeight(node.left) - self.getHeight(node.right)

    def preOrder(self, root):
        if not root:
            return
        print(root.key, end=" ")
        self.preOrder(root.left)
        self.preOrder(root.right)

# Main Program
avl = AVL_Tree()
root = None

# Insert initial elements
elements = [10, 20, 30, 40, 50, 25]
for elem in elements:
    root = avl.insert(root, elem)

# Insert '7' and perform rotations if necessary
root = avl.insert(root, 7)

print("Preorder traversal of AVL tree after inserting 7:")
avl.preOrder(root)

```

## OUTPUT
```
Preorder traversal of AVL tree after inserting 7:
30 20 10 7 25 40 50

```

## RESULT
The Python program successfully performed left rotation in the AVL tree and inserted the element '7', maintaining the AVL balance property
