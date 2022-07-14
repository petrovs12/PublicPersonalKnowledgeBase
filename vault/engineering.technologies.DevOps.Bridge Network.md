---
id: ks6e18pb9z3mctjcsiq0ejm
title: Bridge Network
desc: ''
updated: 1657804999753
created: 1657803180290
---


By default, all cockers run 
in the 'Docker network' (?). Maybe.



Quote from educative:


"By default, **all** containers **run** in the **default network space of Docker**. Hence, **every container can communicate** with others. We can create network isolation if it is needed."



![Docker Network View](/assets/images/2022-07-14-15-15-32.png)


# Default Docker Networks
By default, 3 networks are created:

# host network
Docker Internal- nevermind
# None Network

Docker Internal- nevermind
# Bridge network

named Docker0; it automatically creates IP subnet and gateway.


 **Containers within the docker network can talk to each other via IP addressing**. They are in the **same subnet**.

