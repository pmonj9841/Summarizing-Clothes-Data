# Summarizing-Clothes-Data
'뉴엔*'회사의 데이터를 정리해달라는 부탁을 받았다. 이 회사는 한국 패션사이트에서 판매되는 옷들을 외국인들이 쉽게 둘러보고 구매할 수 있도록 하는 플랫폼을 제공하는 일을 하고 있다. 이 프로젝트에서 사용할 데이터는 고객들이 구매한 제품의 모델명, 브랜드, 출처 사이트를 담고 있다. 각 브랜드와 사이트별로 얼만큼의 상품이 판매되었는지를 파악할 수 있도록 데이터를 정리하였고, 이후에도 유사한 작업을 할 수 있도록 코드를 제공하였다.


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




## How many clothes have been sold in each site?
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




## Exploring data in spreadsheet
변경된 데이터를 내보내어 스프레트시트의 피벗테이블을 통해 더 쉽게 데이터를 살펴볼 수 있도록 하였다.

```python
# Export data
data.to_csv('crawl_modified.csv', index=False)
```
<img src="![스크린샷 2024-02-07 011601](https://github.com/pmonj9841/Summarizing-Clothes-Data/assets/61530808/f3c4da47-5452-4e92-9d15-d86b8374a636)" width="700" height="500">

![스크린샷 2024-02-07 011519](https://github.com/pmonj9841/Summarizing-Clothes-Data/assets/61530808/89eb657c-6431-4d55-bf1e-b24bea02a22d)
