# Ex. No: 16A - Constructing and Printing an AVL Tree in Python

## AIM:
To write a Python program to construct an **AVL tree** and print the nodes of it using the appropriate packages and built-in function.

---

## ALGORITHM:

**Step 1**: Start the program.

**Step 2**: Define a function `getDictTree(tree)` to return the **dict_tree** of an AVL tree.

**Step 3**: Define a function `Construct_AVL(L)` to:
- Create an **AVL tree** from the list `L`.
- Get and print the **dict_tree** using `getDictTree(tree)`.

**Step 4**: Define a list `L` with integer values.

**Step 5**: Call `Construct_AVL(L)` to build the tree and print the result.

**Step 6**: End the program.

---

## PYTHON PROGRAM
```
# Reg.No: 212223060057
# Name: DINESH KUMAR A
# Ex.No: 16A - Constructing and Printing an AVL Tree in Python

from binarytree import bst

def getDictTree(tree):
    return tree.to_dict()

def Construct_AVL(L):
    print("Original List:", L)
    # Build AVL tree from sorted list
    tree = bst(L)
    print("\nConstructed AVL Tree:")
    print(tree)
    print("\nAVL Tree as dictionary:")
    print(getDictTree(tree))

# Main program
L = [10, 20, 30, 40, 50, 25]
Construct_AVL(L)

```

## OUTPUT
```
Original List: [10, 20, 30, 40, 50, 25]

Constructed AVL Tree:
      30
    /    \
  20      40
 /       /  \
10      25   50

AVL Tree as dictionary:
{'value': 30, 'left': {'value': 20, 'left': {'value': 10, 'left': None, 'right': None}, 'right': None}, 'right': {'value': 40, 'left': {'value': 25, 'left': None, 'right': None}, 'right': {'value': 50, 'left': None, 'right': None}}}

```

## RESULT
Thus, the Python program to construct and print an AVL tree using built-in functions was successfully executed and verified.
