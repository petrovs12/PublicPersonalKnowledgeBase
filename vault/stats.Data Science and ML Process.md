---
id: tyuwjv75f6as45qeti6qhsx
title: Data Science and ML Process
desc: ''
updated: 1645912884727
created: 1645907363147
---

```mermaid
graph LR;

a[Data Collection] -->b[Data Preparation] --> c[Model Training] --> d[Model Evaluation/Selection] --> e[Model Persistence]
req[Requests]-->ms[Model Serving]
ms-->ml[Model Logging]
ms<-.->g
ms<-.->f





b-->f[Feature Store]
c-->g[Model Store]
```



# Data Science Process Diagram
