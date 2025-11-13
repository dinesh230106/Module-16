# Ex. No: 16C - Inserting Nodes in a B-Tree in Python

## AIM:
To write a Python function `def insert(self, k):` to insert the nodes in a **B-Tree**.

---

## ALGORITHM:

**Step 1**: Start the program.

**Step 2**: Define the `BTreeNode` class to represent a node:
- Contains a list of keys.
- Contains a list of children.
- Indicates whether it is a leaf.

**Step 3**: Define the `BTree` class with:
- Methods for inserting keys.
- Handling node splitting.
- Tree traversal and printing.

**Step 4**: Implement `insert()`:
- Insert a key into the tree.
- Handle full root case and invoke node splitting if needed.

**Step 5**: Implement `insert_non_full()` to insert a key into a node that is not full.

**Step 6**: Implement `split_child()` to split a full child during insertion.

**Step 7**: Define `print_tree()` to recursively print the structure of the B-Tree.

---

## PYTHON PROGRAM

```
# Reg.No: 212223060057
# Name: DINESH KUMAR A
# Ex.No: 16C - Inserting Nodes in a B-Tree in Python

class BTreeNode:
    def __init__(self, t, leaf=False):
        self.t = t  # minimum degree
        self.leaf = leaf
        self.keys = []
        self.children = []

class BTree:
    def __init__(self, t):
        self.root = BTreeNode(t, True)
        self.t = t

    def insert(self, k):
        root = self.root
        if len(root.keys) == 2*self.t - 1:
            new_root = BTreeNode(self.t)
            new_root.children.append(self.root)
            self.split_child(new_root, 0)
            self.root = new_root
        self.insert_non_full(self.root, k)

    def insert_non_full(self, node, k):
        i = len(node.keys) - 1
        if node.leaf:
            node.keys.append(0)
            while i >= 0 and k < node.keys[i]:
                node.keys[i+1] = node.keys[i]
                i -= 1
            node.keys[i+1] = k
        else:
            while i >= 0 and k < node.keys[i]:
                i -= 1
            i += 1
            if len(node.children[i].keys) == 2*self.t - 1:
                self.split_child(node, i)
                if k > node.keys[i]:
                    i += 1
            self.insert_non_full(node.children[i], k)

    def split_child(self, parent, i):
        t = self.t
        node = parent.children[i]
        new_node = BTreeNode(t, node.leaf)
        parent.keys.insert(i, node.keys[t-1])
        parent.children.insert(i+1, new_node)
        new_node.keys = node.keys[t: ]
        node.keys = node.keys[:t-1]
        if not node.leaf:
            new_node.children = node.children[t:]
            node.children = node.children[:t]

    def print_tree(self, node=None, level=0):
        node = node or self.root
        print("Level", level, ":", node.keys)
        for child in node.children:
            self.print_tree(child, level + 1)

# Main program
bt = BTree(2)  # Minimum degree t=2
elements = [10, 20, 5, 6, 12, 30, 7]

for elem in elements:
    bt.insert(elem)

print("\nB-Tree structure after insertions:")
bt.print_tree()

```

## OUTPUT
```
Level 0 : [10, 20]
Level 1 : [5, 6, 7]
Level 1 : [12]
Level 1 : [30]

```

## RESULT
Thus, the Python program to insert nodes in a B-Tree and display its structure has been successfully executed.
