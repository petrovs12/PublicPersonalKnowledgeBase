---
id: stlANyohtrErNy8tZXnni
title: Quad Tree
desc: ''
updated: 1642522058298
created: 1642521622005
---


Use a 'geographical quad-tree' to store all the locations of all the __things of interest__. The quad-tree is a tree where each node is a rectangle of size 2x2. Each node (except terminal ones) represents a location, and it's children split it into a southeast, northeast, northwest, and southwest quadrant.


So then a quad-tree is like a 2d version of the binary tree.

# Parent Nodes links or Sibling Linked list connections
So we can more easily expand the search area: search up, then do DFS/BFS from there.
With the sibling linked list- also clear what to do.
