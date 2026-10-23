# Populating-Next-Right-Pointers-in-Each-Node
"""
# Definition for a Node.
class Node:
    def __init__(self, val: int = 0, left: 'Node' = None, right: 'Node' = None, next: 'Node' = None):
        self.val = val
        self.left = left
        self.right = right
        self.next = next
"""
class Solution:
    def connect(self, root: 'Optional[Node]') -> 'Optional[Node]':
        if root is None:
            return None
        def add(root):
            if root is None:
                return
            if root.left:
                root.left.next=root.right
                if root.next:
                    root.right.next=root.next.left
            add(root.left)
            add(root.right)
        add(root)
        return root
