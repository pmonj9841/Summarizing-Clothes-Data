# Summarizing Clothes Data
I was asked to organize data from a company, 'NewN*.' This company is providing a platform where foreigners can look through and purchase clothes from Korean websites. Data used in this project includes model names, their brands, and sources. I organized data so that they could see how many products had been sold for each brand and on each site.


```python
import pandas as pd
import matplotlib.pyplot as plt
```
```python
# Load data
data = pd.read_csv('crawl.csv', header=None, sep='\t')
data.columns = ['Site', 'Brand', 'Product']
data.head()
```
![스크린샷 2024-02-07 004216](https://github.com/pmonj9841/Summarizing-Clothes-Data/assets/61530808/30c7a21b-af44-4736-92b0-c2f0274f57be)




## How many clothes have been sold for each brand?
```python
# Count the values
Brand_counts = data['Brand'].value_counts()
# Print top 10
print(Brand_counts.head(10))
```
![스크린샷 2024-02-07 010802](https://github.com/pmonj9841/Summarizing-Clothes-Data/assets/61530808/05c82a50-2461-485f-a5f4-1f3e9dd63dbd)




## How many clothes have been sold on each site?
```python
# Make the values from the same sites identical
for index, a in enumerate(data['Site']):
    parts = a.split('/')
    data.loc[index, 'Site'] = parts[2]

data.head()
```
![스크린샷 2024-02-07 010915](https://github.com/pmonj9841/Summarizing-Clothes-Data/assets/61530808/5bc91a29-0544-4338-9d43-73751d1236b1)

```python
# Count the values
Site_counts = data['Site'].value_counts()
print(Site_counts)
```
![스크린샷 2024-02-07 011009](https://github.com/pmonj9841/Summarizing-Clothes-Data/assets/61530808/1abde97f-6acb-418e-850b-f6c1549c901b)

```python
plt.figure(figsize=(12,5))
plt.bar(Site_counts.index, Site_counts.values)
plt.title('How many clothes have been sold in each site?')
plt.xlabel('Sites')
plt.ylabel('Number of clothes sold')
```
![스크린샷 2024-02-07 011127](https://github.com/pmonj9841/Summarizing-Clothes-Data/assets/61530808/f66f18a8-ac60-4e20-900a-7ecfed10e673)




## Exploring data in a spreadsheet
Let's export the modified data to use the pivot table in a spreadsheet; this will allow us to look through the information more conveniently.

```python
# Export data
data.to_csv('crawl_modified.csv', index=False)
```
![스크린샷 2024-02-07 011601](https://github.com/pmonj9841/Summarizing-Clothes-Data/assets/61530808/f3c4da47-5452-4e92-9d15-d86b8374a636)

![스크린샷 2024-02-07 011519](https://github.com/pmonj9841/Summarizing-Clothes-Data/assets/61530808/89eb657c-6431-4d55-bf1e-b24bea02a22d)
