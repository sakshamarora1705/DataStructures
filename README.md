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

<h4> Implementing a binary search tree </h4>
<code> 
  class Node():
      Node left, right
      int data
  
      def __init__(self, data):
          self.data = data

      #Function to insert a given value to the binary search tree
      def insert(self, value):
          if (value <= self.data):
              if (self.left is None):
                  self.left = new Node(value)
              else:
                  self.left.insert(value)
          else:
              if (self.right is None):
                  self.right = new Node(value)
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
      def printInOrderTraversal():
          if (self.left is not None):
              self.left.printInOrderTraversal()
          
          print(self.data)
  
          if (self.right is not None):
              self.right.printInOrderTraversal()
          
  
              

</code>
