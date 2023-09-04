---
id: xokdu87m4jy6l8994szc098
title: Token Masking
desc: ''
updated: 1689691256554
created: 1689682251868
---


# Token Masking
Mask some words in a sequence and predict which tokens should replace that...
e.g. 

```python
from transformers import pipeline
classifier = pipeline("fill-mask")

classifier("Paris is the [MASK] of France.")
```


No, really 
