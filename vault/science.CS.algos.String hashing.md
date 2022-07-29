---
id: ylepk15iub1sb8kqmxom67i
title: String hashing
desc: ''
updated: 1659107161425
created: 1659106935436
---


# Rolling Polynomial string hashing
Pick a prime p and a large number m, not a multiple of p.
then it's obvious

![](/assets/images/2022-07-29-17-04-15.png)


We can also quickly calsulate the hashes of substrings.

Idk if we can also quickly check for partial matches (i.e. given a string and a potential partial string, check if really is partial).
I suppose it's not difficult...
#todo think about this and read more from [the cp algorithms page](https://cp-algorithms.com/string/string-hashing.html#search-for-duplicate-strings-in-an-array-of-strings)
s