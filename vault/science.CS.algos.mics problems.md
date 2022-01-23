---
id: BOy4GLBQlse9SzjLAlwqp
title: mics problems
desc: ''
updated: 1642937774228
created: 1641981602342
---


# Least Common Ancestor

#TODO 

[Read this and rephrase solution](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/solution/)


# Leetcode 507. Perfect Number

A perfect number is a number that is equal to the sum of its positive divisors, excluding the number itself.
let $x$ is a number.
Let's think about $n=kl$ then sm(kl)=sm(k)*sm(l)+k+l (?).
Example:
$sm(4) = sm(2)*sm(2)+2$



# [Exclusive time of Functions](https://leetcode.com/problems/exclusive-time-of-functions/)

* Process logs in order and put them in a stack
* 'start' log is opening bracket
*  we keep 'time wasted' variable, initialized at 0. It is always re-initializied at 0 whenever the stack is empty. So the 'slate is clean'
* 'end' log is closing bracket. If we get an end log, then the previous one is it's 'start' counterpart. Record time $time(end)+1-time(start)-timeWasted$ for this process in the array. 
Reason for the timeWasted is this time was actually used up by other processes and accounted for already. Reason for +1 is just the way the problem does the bookkeeping, i.e. start 1 means 'start at BEGINNING of period 1', while end 2 means 'end at END of period 2'.
 We then re-initialize timeWasted as simply $time(end)-time(start)+1$ is stack is non-empty ans $0$ is stack is empty.
 * O(n) time, O(n) space
 

[Custom Sort String](https://leetcode.com/problems/custom-sort-string/)

We're given 2 strings, 1 of the order and 1 of the actual string. have to re-sort the actual string like the order is sorted.
```
Input: order = "cba", s = "abcd"
Output: "cbad"

```

Use a Counter to represent the actual string and re-build from scratch in an obvious way. 
need also a $set$ to hold the chars in the string, but not
in the order.

[Toposort solution also possible, check it out.](https://leetcode.com/problems/custom-sort-string/discuss/1704409/Python-3-solutions-(hashmap-lambda-in-sort-and-Topological-sort))


#TODO 

[Balance a Binary Search Tree](https://leetcode.com/problems/balance-a-binary-search-tree/)

Algorithm:
* Build a sorted array via in-order (left,top,right) traversal of the tree.
* Re-build a new tree from the array.
```{python}
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def balanceBST(self, root: TreeNode) -> TreeNode:
        # step 1: build arr via in-order traversal
        arr = []
        
        def dfs(nd):
            if not nd:
                return
            dfs(nd.left) #left
            arr.append(nd.val)# root 
            dfs(nd.right)# right
        dfs(root)
        print(f"{arr=}")# check
        assert sorted(arr) == arr # check

        # step 2: re-build tree recursively from arr
        n= len(arr)
        # take care for off-by-one errors
        def build(lo=0,hi= n):
            if lo>=hi:
                return None
            else:
                mid = (lo+hi)//2
                curr = TreeNode(arr[mid])
                curr.left = build(lo=lo,hi=mid)
                curr.right = build(lo=mid+1,hi=hi)
                
                return curr
        return build()
            
```

[Shortest Path in Binary Matrix](https://leetcode.com/problems/shortest-path-in-binary-matrix/submissions/).

Simple BFS. Maybe can use A* to be fast but idk.


```{python}
class Solution:
    def shortestPathBinaryMatrix(self, grid: List[List[int]]) -> int:
        # idea:
        # use bfs
        m = len(grid)
        n = len(grid[0])
        def getNeighbors(cell): #O(1)
            i,j = cell[0],cell[1]
            return [(i+k,j+l) for k in range(-1,2) for l in range(-1,2) if 
                   abs(k)+abs(l)>=1 and 0<=k+i<m and 0<=j+l<n 
                    and grid[i+k][j+l]==0
                   ]
        if (grid[0][0]!=0) or (grid[m-1][n-1]!=0):
            #print(f"no end or beginning,{grid[0][0]=},{grid[m-1][n-1]=}")
            return -1
        # note: when we see a cell, we never need to update the distance to it!!
        from queue import deque
        q = deque()
        seen = dict()
        q.append(((0,0),1))
        while q:
            cell,dist = q.popleft()
            if cell in seen:
                continue
            else:
                seen[cell]=dist
            potentialNeighbors=getNeighbors(cell)
           # print(f"{cell=},{potentialNeighbors=}")
            for nb in potentialNeighbors:
                if nb==(n-1,m-1):
                    return dist+1
                if nb not in seen:
                    q.append((nb,dist+1))
                
            
            
        if (m-1,n-1) in seen:
            return seen[(m-1,n-1)]
        else:
            return -1
```

[Employee Free Time](https://leetcode.com/problems/employee-free-time/)


Employee free time problem:

We are given a list schedule of employees, which represents the working time for each employee.

Each employee has a list of non-overlapping Intervals, and these intervals are in sorted order.

Return the list of finite intervals representing common, positive-length free time for all employees, also in sorted order.

Solution:
start w/ free interval $(-\infty,\infty)$. Make a priority queue of intervals from teh emp schedule list.
Repeadedly choose the employee schedule item w/ the earliest start time..
Then:
* if the end time of the current interval is less than the start time of the current free interval, do nothing 

* if the end time of the current free interval is smaller than the start tiem of employe interval, add current to solution, re-initialize new to point to end time of employee
* if overlap with emp.start< current.start, then update current.start to emp.end. If needed, update current.end as well

* if overlap with emp.start>current.start, can add
(current.start,emp.start)  to solution and update current to start at emp.end. The end $\infty$ if emp.end> current.end, else current.end.

[Skyline](https://leetcode.com/problems/the-skyline-problem/)

Approach - put all buildings in a priority queue, sorted by start time. Bellow instructions skip some corner cases, as they are very verbose (but are in code).

* Initialize 'current' as $-\infty,\infty,0$ (the default building), sky(result) to empty list.
* Pop the queue. Call this proc. If current.end < proc.start,
add current to skyline. if $current.start < proc.start<=current.end$, then :
 * if current.height > proc.height, update start of proc to be $current.end$, and add back to queue.
 * if $current.height<proc.height$ , add current to skyline, check if need to add $proc.end,current,start,current.height$ to queue.
 * in the end add the last one if needed.

 Be careful with corner cases, e.g. when 2 heights are the same, with deleting the first dummy building, and adding the last building if needed. 
 ```{python}
 from heapq import heappop, heappush
class Solution:
    def getSkyline(self, buildings: List[List[int]]) -> List[List[int]]:
        # make a priority q w/ all buildings. We
        q = []
        for b in buildings:
            heappush(q,b)
        res = []
        # start, end, height
        current = [float("-inf"),float("inf"),0]
        while q:
            proc = heappop(q)
            s,e,h = proc[0],proc[1],proc[2]
            if s>current[1]:
                
                res.append([current[0],current[2]])# finalize a 'current'
                current = [s,e,h]
            if s==current[1]:
                # case 1:
                # if heights are different:
                if h!=current[2]:
                    res.append([current[0],current[2]])# finalize a 'current'
                    current = [s,e,h]
                else:
                    current[1] = e
                    continue
                    
            else:
                # the new one is higher:
                if current[2]<h:
                    if  current[0]<s:
                        res.append([current[0],current[2]])
                    
                    if current[1]>e:# if old one continues after current one, add it back to queue
                        heappush(q,[e,current[1],current[2]])
                    else:# do nothing, it will be swallowed
                        pass
                    current = [s,e,h]
                    
                # same height
                elif current[2]==h:# update end time of current
                    current[1] = max(e,current[1])
                else:# old one is higher
                    if e>current[1]:
                        heappush(q,[current[1],e,h])
        # notice we only add stuff after finishing the processing, so we'll be left
        # with somethign to add in the end
        if current[0]>res[-1][0]:
            res.append([current[0],current[2]])
        res2 = []
        for r in res[1:]:
            if not res2 or r[1]!=res2[-1][1]:
                res2.append(r)
        return res2
                    
                    
                
            
        
 ```


