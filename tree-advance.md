# Tree Data Structure (DSA)

## 1. Level Order Traversal
In **Level Order Traversal**, the nodes are visited level by level from left to right. It is also called **Breadth-First Search (BFS)**. It can be implemented using a queue:
```
void levelOrder(Node root) {
    if (root == null) return;
    Queue<Node> queue = new LinkedList<>();
    queue.add(root);
    while (!queue.isEmpty()) {
        Node current = queue.poll();
        System.out.print(current.data + " ");
        if (current.left != null) queue.add(current.left);
        if (current.right != null) queue.add(current.right);
    }
}
```

## 2. Breadth-First Search (BFS)
**BFS** explores all the nodes at the current depth level before moving to the next level. It is typically implemented using a queue (as shown above in Level Order Traversal).

## 3. Depth-First Search (DFS)
**DFS** explores as far as possible along a branch before backtracking. It has three variations based on the order of traversal:
1. Preorder
2. Inorder
3. Postorder

Example of Preorder Traversal:
```
void preorder(Node root) {
    if (root == null) return;
    System.out.print(root.data + " ");
    preorder(root.left);
    preorder(root.right);
}
```

## 4. Count of Nodes
The **Count of Nodes** is the total number of nodes in the tree. It can be calculated recursively:
```
int countNodes(Node root) {
    if (root == null) return 0;
    return 1 + countNodes(root.left) + countNodes(root.right);
}
```

## 5. Sum of Nodes
The **Sum of Nodes** is the sum of values of all nodes in the tree. It can be calculated recursively:
```
int sumNodes(Node root) {
    if (root == null) return 0;
    return root.data + sumNodes(root.left) + sumNodes(root.right);
}
```

## 6. Height of Tree
The **Height of a Tree** is the number of edges on the longest path from the root to a leaf node. It can be calculated recursively:
```
int height(Node root) {
    if (root == null) return 0;
    return 1 + Math.max(height(root.left), height(root.right));
}
```

## 7. Diameter of Tree
The **Diameter of a Tree** is the length of the longest path between any two nodes in the tree. It can be calculated as:
```
int diameter(Node root) {
    if (root == null) return 0;
    int leftHeight = height(root.left);
    int rightHeight = height(root.right);
    int leftDiameter = diameter(root.left);
    int rightDiameter = diameter(root.right);
    return Math.max(leftHeight + rightHeight + 1, Math.max(leftDiameter, rightDiameter));
}
```

## 8. Subtree of Another Tree
To check if a tree is a subtree of another, compare the root and recursively check:
```
boolean isSubtree(Node s, Node t) {
    if (t == null) return true;
    if (s == null) return false;
    if (isIdentical(s, t)) return true;
    return isSubtree(s.left, t) || isSubtree(s.right, t);
}

boolean isIdentical(Node s, Node t) {
    if (s == null && t == null) return true;
    if (s == null || t == null) return false;
    return (s.data == t.data && isIdentical(s.left, t.left) && isIdentical(s.right, t.right));
}
```


