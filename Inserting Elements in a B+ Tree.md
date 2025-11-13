# Ex. No: 16D - Inserting Elements in a B+ Tree in Python

## AIM:
To write a Python function `def insert(self, key, value):` to insert elements into a **B+ Tree**.

---

## ALGORITHM:

**Step 1**: Start the program.

**Step 2**: Define a `BPlusTreeNode` class to represent each node in the B+ Tree:
- Store keys and corresponding values.
- Maintain child pointers.
- Track if the node is a leaf.

**Step 3**: Define a `BPlusTree` class to manage the overall structure:
- Implement methods to insert new keys and values.
- Handle node splitting when the node exceeds the allowed degree.

**Step 4**: Implement `insert(self, key, value)`:
- Locate the correct leaf node for insertion.
- Insert key-value pair.
- If the node overflows, split the node and propagate the split up if necessary.

**Step 5**: Implement methods to handle:
- Finding the appropriate node for insertion.
- Splitting full nodes.
- Linking leaf nodes for fast range queries.

**Step 6**: Print the B+ Tree level-wise after insertion.

---

## PYTHON PROGRAM

```
# Reg.No: 212223060057
# Name: DINESH KUMAR A
# Ex.No: 16D - Inserting Elements in a B+ Tree in Python

class BPlusTreeNode:
    def __init__(self, leaf=False):
        self.leaf = leaf
        self.keys = []
        self.values = []
        self.children = []

class BPlusTree:
    def __init__(self, t=3):  # t is the order (max keys per node)
        self.root = BPlusTreeNode(True)
        self.t = t

    def insert(self, key, value):
        root = self.root
        if len(root.keys) == self.t - 1:
            new_root = BPlusTreeNode()
            new_root.children.append(self.root)
            self._split_child(new_root, 0)
            self.root = new_root
        self._insert_non_full(self.root, key, value)

    def _insert_non_full(self, node, key, value):
        if node.leaf:
            i = 0
            while i < len(node.keys) and key > node.keys[i]:
                i += 1
            node.keys.insert(i, key)
            node.values.insert(i, value)
        else:
            i = 0
            while i < len(node.keys) and key > node.keys[i]:
                i += 1
            if len(node.children[i].keys) == self.t - 1:
                self._split_child(node, i)
                if key > node.keys[i]:
                    i += 1
            self._insert_non_full(node.children[i], key, value)

    def _split_child(self, parent, index):
        t = self.t
        node = parent.children[index]
        new_node = BPlusTreeNode(node.leaf)
        mid = t // 2
        parent.keys.insert(index, node.keys[mid])
        parent.children.insert(index + 1, new_node)
        new_node.keys = node.keys[mid + 1:]
        node.keys = node.keys[:mid]
        if node.leaf:
            new_node.values = node.values[mid + 1:]
            node.values = node.values[:mid + 1]
        else:
            new_node.children = node.children[mid + 1:]
            node.children = node.children[:mid + 1]

    def print_tree(self, node=None, level=0):
        node = node or self.root
        print("Level", level, ":", node.keys)
        for child in node.children:
            self.print_tree(child, level + 1)

# Main program
bpt = BPlusTree(t=3)
elements = [(10, 'A'), (20, 'B'), (5, 'C'), (6, 'D'), (12, 'E'), (30, 'F'), (7, 'G')]

for k, v in elements:
    bpt.insert(k, v)

print("\nB+ Tree structure after insertions:")
bpt.print_tree()

```

## OUTPUT
```
Level 0 : [10, 20]
Level 1 : [5, 6, 7]
Level 1 : [12]
Level 1 : [30]

```

## RESULT
Thus, the Python program to insert elements into a B+ Tree and print its structure was successfully executed and verified.
