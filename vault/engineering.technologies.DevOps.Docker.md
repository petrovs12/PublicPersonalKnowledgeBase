---
id: 1loz9aicjxuj3shpwllwsnp
title: Docker
desc: ''
updated: 1657798610159
created: 1657796712724
---


These are rough notes from the Educative Tools

# Why Docker

Problem:
dependency, environment managementm

Scaling 

Updates



# Basics

* Container- isolated instance of a running VM.
* Image 'recipe' for building a container. 
* Registry - Repository for imates.


Can run containers from existing images.
Can craete new images.
Can upload images to registries


# Orchestrator and updates


## Scale-up


```mermaid
graph LR;
R["Registry(app v1.0.0,app v1.0.1)"];
RP[Reverse Proxy];
O[Orchestrator];
S1["Server 1, app v1.0.1"];
S2["Server 2, app v1.0.1"];
S3["Server 3, app v1.0.1"];
S4["Server 4, app v1.0.1"];


R-->O
O-->RP
O-->S1
O-->S2
O-->S3
O-->S4
RP-->S1
RP-->S2
RP-->S3
RP-->S4
```

[[engineering.technologies.Proxy and Reverse Proxy]]

#TODO Question: does the reverse proxy talk to the orchestrator??



## Updates

An orchestrator is something that sits in front of a bunch of containers of the same type and:
1. Redirects traffic to the correct container.
2. Runs more or deletes containers
3. Updates containers by a schedule (?)...

So probably docker allows "seamless" updates via it's orchestrator..


**Solves  dependency conflicts- every container is 'born' to run tightly coupled set of applications/services.**. Most of the time it will be a single application.



