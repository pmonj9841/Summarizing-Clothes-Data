# Summarizing-Clothes-Data
In this project, data about clothes sold online are summarized so that a company can see which brands of clothes have been sold and on which site.



```python
import pandas as pd
import matplotlib.pyplot as plt

# Load data
data = pd.read_csv('crawl.csv', header=None, sep='\t')
data.columns = ['Site', 'Brand', 'Product']
data.head()
```

![스크린샷 2024-02-07 004216](https://github.com/pmonj9841/Summarizing-Clothes-Data/assets/61530808/30c7a21b-af44-4736-92b0-c2f0274f57be)
