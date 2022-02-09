---
id: 0FaG1aU68OaRkl5IK6xhh
title: Graph Traversal
desc: ''
updated: 1643451522115
created: 1641835100590
---


# 


# Basic Tree Traversals
## DFS

T-top(or root)
L=left
R=right


[Tree traversals](https://www.geeksforgeeks.org/tree-traversals-inorder-preorder-and-postorder/)
### Pre-order
T, L , R 
### In-order
L, T, R
### Post-order :
L R T

## BFS 
### Iteratively deepening BFS


## Heuristic Search
### A*
 consisten heuristic


# DFS Notes

Exploring w/ dfs
```{python}

seen = set()
def explore(V:List[Int],E:Dict[Int,Set[int]],v):
    if v in seen:  #optionally!!!
        return
    seen.add(v)
    previsit(v) # optionally! use if need to detect cycles, other stuff 
    for w in E[v]:
        explore(V,E,w)
    postvisit(v) # optionally! useful to keep track of cycles and other stuff

```

Intuition:
 Explore labyrinth: need some __rope__ (stack) and __piece of chalk__(visited set). Go along the __rightmost path without chalk marks__ (dfs ordering), and return when 
 you reach a dead end.

 ### Previsit and connected components

 ```{python}
 #...
 cc=dict()
 def previsit(v,cc):
    ccnum[v] = cc
 ```






  
   

