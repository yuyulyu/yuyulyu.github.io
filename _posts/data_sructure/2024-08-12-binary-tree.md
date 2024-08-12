---
title: Binary Tree
description: Write down description here.
author: yoyo
date: 2024-08-12 11:33:00 +0800
categories: [Data Structure and Algorithm, Algorithm]
tags: [binary tree]
---

A binary tree is a tree data structure in which each node has at most two children, which are referred to as the left child and the right child. 

【image】structure-of-binary-tree-1
- Root: The top node in a tree.
- Parent Node: Any node except the root.
- Child Node: A node directly connected to another node when moving away from the Root.
- Leaf Node: A node with no children.
- Siblings: Nodes with the same parent.
- Depth: The length of the path to its root.
- Height: The depth of the deepest node.
  
## How binary tree stored in memory

Binary trees can be stored in memory using two common representations: **pointer-based (linked) structures** and **array-based structures**.

### <ins>Pointer-Based Storage (Linked Storage)</ins>

In pointer-based storage, each node is an object, and each node typically contains:

- **Data**: The value or information contained in the node.
- **Left Child Pointer**: A pointer to the left child node.
- **Right Child Pointer**: A pointer to the right child node.

```python
class BinaryTree:
    def __init__(self, value):
        self.val = value  # The value or information contained in the node.
        self.left = None  # A pointer to the left child node.
        self.right = None  # A pointer to the right child node.
```

This method is dynamic, allowing the tree to expand as needed. It is particularly useful for operations that involve **frequent insertions and deletions**, as nodes can be added or removed without reorganizing the entire structure.

### <ins>Array-Based Storage</ins>

In array-based storage of binary trees:
- **Root**: The root element is stored at the beginning of the array.
- **Left Child**: The left child of a node located at position n is found at position 2n + 1.
- **Right Child**: The right child of a node located at position n is found at position 2n + 2.

【image】

This method is **space-efficient** when the tree is **complete and perfect**, as it doesn't require any pointers. However, for sparse trees, this method can waste memory space due to empty indices in the array representing absent nodes.

Array storage is particularly efficient for binary heaps and other binary trees that require accessing children and parents in constant time during insertions and deletions.

```python
class ArrayBasedBinaryTree:
    def __init__(self):
        self.tree = []  # Initialize an empty list to store tree elements

    def root(self, value):
        """Insert root node"""
        if not self.tree:
            self.tree.append(value)  # Insert root if tree is empty

    def insert_left(self, parent_index, value):
        """Insert left child"""
        child_index = 2 * parent_index + 1
        if child_index < len(self.tree):
            self.tree[child_index] = value
        else:
            # Extend the list with None to maintain structure
            while len(self.tree) <= child_index:
                self.tree.append(None)
            self.tree[child_index] = value

    def insert_right(self, parent_index, value):
        """Insert right child"""
        child_index = 2 * parent_index + 2
        if child_index < len(self.tree):
            self.tree[child_index] = value
        else:
            # Extend the list with None to maintain structure
            while len(self.tree) <= child_index:
                self.tree.append(None)
            self.tree[child_index] = value

    def display(self):
        """Display the tree"""
        return self.tree
```


## Different types of binary tree

Different types of binary trees are designed to meet specific needs, such as maintaining balance or optimizing search operations.

| Binary Tree | Applications |
|-------------|--------------|
| Full Binary Trees | Often used in applications that require a simple and efficient tree structure without complex operations.|
| Complete Binary Trees | Ideal for priority queues and heap-based algorithms, where quick access to elements is necessary. |
| Binary Search Trees (BST) | Serve well in database indexing systems where quick insertion, deletion, and retrieval of records are frequent.|
| AVL Trees | In applications where low latency data retrieval is critical, such as in network routers, where balancing ensures optimal search times.|

### Full Binary Tree

A full binary tree is a type of binary tree in which every node other than the leaves has two children. In other words, each node has exactly zero or two children. 
- Every node has 0 or 2 children.
- Leaves are at the same level or one level apart.

【image】full-binary-tree

### Complete Binary Tree

A complete binary tree is a type of binary tree in which all levels, except possibly the last, are completely filled, and all nodes are as left as possible. This arrangement makes complete binary trees ideal for being stored in an array, as their compact and left-filled structure reduces the space complexity.
- All levels are fully filled except possibly the last level.
- Nodes are positioned as far left as possible.

【image】complete-binary-tree

### Binary Search Tree (BST)

A  binary tree in which for each node, the left children are less than the node and the right children are greater. This property makes BSTs immensely useful for search and retrieval operations, as the decision tree of going left or right at each step significantly cuts down the search space.
- The left subtree of a node contains only nodes with keys lesser than the node’s key.
- The right subtree of a node contains only nodes with keys greater than the node’s key.
- There must be no duplicate nodes.

### Adelson-Velsky and Landis (AVL) Tree
A self-balancing binary search tree where the height of the two child subtrees of any node differ by no more than one. If at any time the heights differ more than one, rebalancing is done to restore this property. AVL trees are optimized for lookup-intensive applications, where frequent insertions and deletions necessitate quick rebalancing to maintain efficient search times.

#### Balance factor

The balance factor helps in determining the type of rotation needed to maintain the tree's balance. It must always be -1, 0, or +1.

**Balance factor (node) = height(right subtree) - height(left tree)**

#### Rebalance AVL tree

When a node is added/deleted to/from an AVL tree, performing rotations is needed to ensure that the balance factor of all nodes remains within the allowed range.

> [Link to note about binary tree](https://yuyulyu.github.io/posts/binary-tree/)
{: .prompt-tip }

## Tree Traversal

### Inorder

### Preorder

### Postorder

### Level Order

### Depth First Search (DFS)

### BFS
