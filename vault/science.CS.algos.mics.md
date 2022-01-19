---
id: XGuPRH9frbFI57K3ZdqVw
title: mics
desc: ''
updated: 1642610669919
created: 1641979954736
---

# 100 Prisoners Problems
[](https://www.youtube.com/watch?v=_X_Q-_X_X_Q)

[youtube](https://www.youtube.com/watch?v=C5-I0bAuEUE)
[Evernote Link](https://www.evernote.com/shard/s101/nl/11122041/2b02fecb-f12e-46ad-a9d7-0a8bc96f3bfa?title=The%20100%20prisoners%20map%20-reduce%20probablistic%20%22analysis%22)
 (First,note that I haven't found a deterministic solution for the problem with "stages buffering", but trying to think of the ways to stochastically analyze the whole thing and how to get the optimum utility of time spend in jail/risk). The note is not very well structured ,if you have some questions (though it's completely useless problem, of course)  please call me.
 So, we assume that we can calculate the interarrival time, but we need a
So, the problem is:
 We are in a prison, and there is this warden ,who gives us the following game: We are prisoners;before the game starts, we can talk to each other, after it starts we can't talk any more.
 At random times ,the warden calls a random prisoner in a room with a light switch, which is initially off;.
 If at any point any of the prisoners announces that all the prisoners have visited the room, then all are free if he(she ?) 's correct.


 # [Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)

 Tortoise and hare algorithm to determine if present. Start from head, and ignore the equality of the 1st node.


Then:
if a nodes, then cycle of b:
hare: $2*t$ 
tortoise:
$t$
then:
$t-a=2*t-a(mod b)$
$t==0(mod b)$
Thus for the intersection node it's true that:
$t-a==-a(mod b)$

Thus if we start from the head of the list, it's position is $1(mod b)$. If we advance $a$ times is $a+1(mod b )$ and in list.
On the other hand, if we start from the intersection node and also advance $a$ times it's position will also be $a+1(mod b)$.
Thus we can initialize 2nd pointer at the beginning, then move by one, until they meet, and that will be the first one.

# [670. Maxiumum Swap](https://leetcode.com/problems/maximum-swap/)

Bookkeeping is a bit ugly, as well as the multiple num->string->list->string->num conversion chain; would be simpler to 
convert directly to list of nums and operate on that.
```{python}
def maximumSwap(num: int) -> int:
    # let the digit representation be a1a2...
    # we want to swap the earliest possible, for which we have a larger one after that, with the largest possible one 
    # after that. So we can start from the back and keep track of the max to right of current, and record last time it 
    # happened that current was not current maximum!
    nm = str(num)
    n = len(nm)
    lastSwapPair=(float("inf"),float("inf"))
    currMaxSeen = float("-inf")
    currMaxSeenIndex = float("inf")
    for i in range(n-1,-1,-1):
        currDigit = int(nm[i])
        # if swap candidate
        if currDigit<currMaxSeen:
            lastSwapPair = (i,currMaxSeenIndex)# simply update the maxSwapPair
        elif currDigit==currMaxSeen:
            continue
        else:
            currMaxSeen = currDigit
            currMaxSeenIndex = i
    #print(f"{currMaxSeen=},{lastSwapPair=},{currMaxSeenIndex=}")
    nm = [c for c in nm]
    #print(nm)
    if lastSwapPair[0]<n:
        tmp = nm[lastSwapPair[0]]
        nm[lastSwapPair[0]] = nm[lastSwapPair[1]]
        nm[lastSwapPair[1]] = tmp
    #print(f"{nm=}")
    return int("".join(nm))
            
```

# [1047. Remove All Adjacent Duplicates In String](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/)

```{python}
def popMultiple(q):
    if q.qsize() <2:
        return
    else:
        k,l = q.get(),q.get()
        if k!=l:
            q.put(l)
            q.put(k)
            return
        else:
            popMultiple(q)
    
    
class Solution:
    def removeDuplicates(self, s: str) -> str:
        # what we could do is to have
        # 2 pointers- current left, current right
        # 3 operations:
        # if delete, 
        # just use a stack
        from queue import LifoQueue
        q = LifoQueue()
        for c in s:
            q.put(c)
            popMultiple(q)
        
        return "".join(q.queue)

```