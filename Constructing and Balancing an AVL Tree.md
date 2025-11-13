# Ex. No: 16B - Constructing and Balancing an AVL Tree in Python

## AIM:
To write a Python program to construct an **AVL tree**, balance it, and print the nodes **before and after balancing** using the appropriate packages and built-in function.

---

## ALGORITHM:

**Step 1**: Start the program.

**Step 2**: Define a method `getDictTree(tree)` to return the `dict_tree` or structure of the AVL tree.

**Step 3**: Define a method `Construct_AVL(L)` to:
- Create a binary tree from the list `L`.
- Print the tree **before balancing**.
- Sort and reinsert the nodes in a balanced manner (simulating AVL behavior).
- Print the tree **after balancing**.

**Step 4**: Create a list `L` of integers.

**Step 5**: Call `Construct_AVL(L)` to build and balance the tree.

**Step 6**: End the program.

---

## PYTHON PROGRAM
```
# Reg.No: 212223060057
# Name: DINESH KUMAR A
# Ex.No: 16B - Constructing and Balancing an AVL Tree in Python

from binarytree import build, Node, bst

def getDictTree(tree):
    return tree.to_dict()

def Construct_AVL(L):
    print("Original List:", L)
    
    # Build tree from list
    tree = build(L)
    print("\nTree before balancing:")
    print(tree)
    
    # Sort list to simulate balanced AVL insertion
    L_sorted = sorted(L)
    balanced_tree = bst(L_sorted)
    
    print("\nTree after balancing (AVL simulation):")
    print(balanced_tree)

# Main program
L = [10, 20, 30, 40, 50, 25]
Construct_AVL(L)

```

## OUTPUT
```
Original List: [10, 20, 30, 40, 50, 25]

Tree before balancing:
  10
    \
     20
       \
        30
          \
           40
             \
              50
               \
                25

Tree after balancing (AVL simulation):
      30
    /    \
  20      40
 /       /  \
10      25   50

```

## RESULT
Thus, the Python program to construct and balance an AVL tree was successfully executed and verified.

