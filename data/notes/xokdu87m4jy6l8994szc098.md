

# Token Masking
Mask some words in a sequence and predict which tokens should replace that...
e.g. 

```python
from transformers import pipeline
classifier = pipeline("fill-mask")

classifier("Paris is the [MASK] of France.")
```



