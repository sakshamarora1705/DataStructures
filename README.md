<h1> Data Structures: Trees </h1>

Trees:
Root node -> Child nodes -> Child nodes -> Leaf nodes

Binary Trees: Each node has no more than two child nodes.
Each node has a left node and a right node.

<h3> Binary Search Tree </h3>
Binary Search Tree: A binary tree that fulfills a specific ordering property, which is, on any subtree:
<ul>
  <li> The left nodes are less than the root node. </li>
  <li> The root node is less than the right nodes. </li>
</ul>

Searching for a value in the tree:


How do inserts work in Binary Search Trees?

<ol>
  <li> Compare the value of the new node with the root node. </li>
  <li> If the value of new node is less than the root node, the new node will be inserted to the left of the root node. </li>
  <li> However, if the value of the new node is greater than the root node, the new node will be inserted to the right of the root node. </li>
  <li> We will keep comparing the value of the new node with the root node of the subtree until we are able to find a suitable place for the new node in the binary search tree. </li>
</ol>
  
Balanced vs. Unbalanced 

Unbalanced tree:
insert: O(n)
find: O(n)

Balanced tree:
insert: O(log n)
find: O(log n)

Traversing a tree:
Inorder: left, root, right (typical)
Preorder: root, left, right
Postorder: left, right, root

<br>
<h3> Implementing a binary search tree </h3>

<pre><code class="python">              
class Node:

    #Initializing the node class
    def __init__(self, data = None):
        self.left = self.right = None
        self.data = data


    #Function to insert a given value to the binary search tree
    def insert(self, value):
        if (value <= self.data):
            if (self.left is None):
                self.left = Node(value)
            else:
                self.left.insert(value)
        else:
            if (self.right is None):
                self.right = Node(value)
            else:
                self.right.insert(value)


    #Function to check if the given value is present in the binary search tree or not
    def contains(self, value):
        if (value == self.data):
            return True
        elif (value < self.data):
            if (self.left is None):
                return False
            else:
                return self.left.contains(value)
        elif (value > self.data):
            if (self.right is None):
                return False
            else:
                return self.right.contains(value)


    #Function to print the inorder traversal of the given binary search tree 
    def printInOrderTraversal(self):
        if (self.left is not None):
            self.left.printInOrderTraversal()
          
        print(self.data)
  
        if (self.right is not None):
            self.right.printInOrderTraversal()
</code></pre>

<br>

<h4> Testing binary search tree implementation </h4>
<pre><code class="python">
>>> root = Node(5)
>>> root.left
>>> root.right
>>> root.insert(9)
>>> root.right.data
9
>>> root.insert(4)
>>> root.left.data
4
>>> root.printInOrderTraversal()
4
5
9
>>> root.insert(10)
>>> root.printInOrderTraversal()
4
5
9
10
>>> root.contains(10)
True
>>> root.contains(1)
False
</code></pre>


<br>

<h2> Interview Questions associated with binary trees </h2>
<p> Subtrees of subtrees are also considered as trees, which is why our functions would be recursive. </p>


<pre><code class="python">
def binaryTreeSum(root):
    if root is None:
        return 0
    else:
        leftTreeSum = binaryTreeSum(root.left)
        rightTreeSum = binaryTreeSum(root.right)
        return root.data + leftTreeSum + rightTreeSum
</code></pre>


<pre><code class="python">
>>> root = Node(5)
>>> root.insert(4)
>>> root.insert(9)
>>> root.insert(6)
>>> root.insert(1)
>>> root.insert(8)
>>> root.insert(3)
>>> root.insert(7)
>>> root.insert(2)
>>> root.printInOrderTraversal()
1
2
3
4
5
6
7
8
9
>>> binaryTreeSum(root)
45
</code></pre>

<br>

<p> 
Q. How to solve (almost) any binary tree coding problem?
<br>
A. Taking a recursive approach:
<ol>
  <li> Finding one or more base cases </li>
  <li> Calling the same function on the left subtree </li>
  <li> Calling the same function on the right subtree </li>
  <li> Combining the two results </li>
</ol>
</p>

Get the max value from the binary tree
<pre><code class="python">
def binaryTreeMax(root):
    if root is None:
        return float("-inf")
    else:
        leftTreeMax = binaryTreeMax(root.left)
        rightTreeMax = binaryTreeMax(root.right)
        return max(root.data, leftTreeMax, rightTreeMax)
</code></pre>

Get the height of the binary tree
<pre><code class="python">
def binaryTreeHeight(root):
    if root is None:
        return 0
    else:
        leftTreeHeight = binaryTreeHeight(root.left)
        rightTreeHeight = binaryTreeHeight(root.right)
        return 1 + max(leftTreeHeight, rightTreeHeight)
</code></pre>

Check if a specific value exists in the tree
<pre><code class="python">
def existsInBinaryTree(root, value):
    if root is None:
        return False
    else:
        inLeftBinaryTree = existsInBinaryTree(root.left, value)
        inRightBinaryTree = existsInBinaryTree(root.right, value)
        return root.data == value or inLeftBinaryTree or inRightBinaryTree
</code></pre>

Reverse a binary tree
<pre><code class="python">
def reverseBinaryTree(root):
    if root is None:
        return
    else:
        reverseBinaryTree(root.left)
        reverseBinaryTree(root.right)
        root.left, root.right = root.right, root.left
</code></pre>


<pre><code class="python">
>>> root = Node(15)
>>> root.insert(8)
>>> root.insert(9)
>>> root.insert(11)
>>> root.insert(14)
>>> root.insert(7)
>>> root.insert(17)
>>> root.insert(19)
>>> reverseBinaryTree(root)
>>> root.printInOrderTraversal()
19
17
15
14
11
9
8
7
</code></pre>


<h5> Binary Tree Longest Consecutive Sequence </h5>
Given a binary tree, find the length of the longest consecutive sequence path.
Hints:
<ul>
  <li> Use recursion to traverse the entire tree. </li>
  <li> Check the parent node for each node and make sure that current node's value is one more than its parent node. </li>
  <li> Update the longest consecutive path at each step. </li>
</ul>
 




