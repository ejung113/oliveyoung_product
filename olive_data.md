#### 올리브영 데이터 전처리



```python
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
import seaborn as sns
```

```python
df = pd.read_csv("olive_data_crawling.csv")
df
```

```html
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>닉네임</th>
      <th>태그</th>
      <th>별점</th>
      <th>작성일</th>
      <th>발색력</th>
      <th>지속력</th>
      <th>수분감</th>
      <th>피부타입</th>
      <th>리뷰</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>혜요미</td>
      <td>복합성\n봄웜톤</td>
      <td>4</td>
      <td>2021.12.11</td>
      <td>보통이에요</td>
      <td>예상보다 짧아요</td>
      <td>보통이에요</td>
      <td>건성에 좋아요</td>
      <td>📦제품상태\n아..올리브영 온라인으로 시키는 물건들 처음 상태가\n좀 별로인 경우가...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>숑댕</td>
      <td>스킨케어 분야 탑리뷰어</td>
      <td>5</td>
      <td>2021.11.23</td>
      <td>아주 만족해요</td>
      <td>지속이 오래돼요</td>
      <td>아주 촉촉해요</td>
      <td>건성에 좋아요</td>
      <td>미 제품 미쳤어요\n저는 여기에 정착하려규요\n리뷰에 가격이 비싸다는 글이 많던데 ...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>여쿨라제품내줘</td>
      <td>지성\n여름쿨톤\n트러블\n홍조</td>
      <td>5</td>
      <td>2021.12.13</td>
      <td>아주 만족해요</td>
      <td>지속이 오래돼요</td>
      <td>아주 촉촉해요</td>
      <td>건성에 좋아요</td>
      <td>🌸여쿨라이트 20호(밝은 21호)🌸\n\n어며들었다..😲\n이러다간 듀틴트까지 구매...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>ho****</td>
      <td>지성\n웜톤\n모공\n블랙헤드</td>
      <td>5</td>
      <td>2021.12.16</td>
      <td>아주 만족해요</td>
      <td>보통이에요</td>
      <td>아주 촉촉해요</td>
      <td>건성에 좋아요</td>
      <td>젤리쿠션이라 그런지 수분감과 쿨링이 아주 맘에 드네요! 얇게 올라가서 스킨케어하는 ...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>yuriful</td>
      <td>메이크업 분야 탑리뷰어</td>
      <td>4</td>
      <td>2021.11.03</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>아주 촉촉해요</td>
      <td>건성에 좋아요</td>
      <td>21호 수부지💖\n올라이브에서 구매했는데 배송 정말 빠르게 왔어요🤭\n슬기 포토카드...</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>523</th>
      <td>523</td>
      <td>ciel****</td>
      <td>NaN</td>
      <td>5</td>
      <td>2021.11.02</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>건성에 좋아요</td>
      <td>촉촉 하면서 가볍고 건성이랑 들뜸 걱정했는데 \n펴버르기도 쉽고 성분도 괜찮아여\n...</td>
    </tr>
    <tr>
      <th>524</th>
      <td>524</td>
      <td>jenn****</td>
      <td>NaN</td>
      <td>5</td>
      <td>2021.10.31</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>복합성에 좋아요</td>
      <td>너무 건조한걸 쓰면 떠버리는데 이상품은 안그런  것 같아요\n\n다음에 또 재구매 ...</td>
    </tr>
    <tr>
      <th>525</th>
      <td>525</td>
      <td>alsgmlwk****</td>
      <td>NaN</td>
      <td>5</td>
      <td>2021.10.30</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>아주 촉촉해요</td>
      <td>건성에 좋아요</td>
      <td>환절기에 사용하기 좋은 촉촉이 쿠션입니다. 그렇다고 해서 마스크에 묻어남이 많다거나...</td>
    </tr>
    <tr>
      <th>526</th>
      <td>526</td>
      <td>dmsdl****</td>
      <td>NaN</td>
      <td>5</td>
      <td>2021.10.30</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>복합성에 좋아요</td>
      <td>전에 버전은 만족했는데 저렴하게 구매해서 좋아요 이것도 좋겠주ㅡ</td>
    </tr>
    <tr>
      <th>527</th>
      <td>527</td>
      <td>tk****</td>
      <td>NaN</td>
      <td>4</td>
      <td>2021.11.05</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
     <td>복합성에 좋아요</td>
      <td>어뮤즈 팩트 사용하고 있어서 새로나와서 구매해봤어요\n아직 사용은 안해봤는데 리뷰보...</td>
    </tr>
  </tbody>
</table>
```

<p>528 rows × 10 columns</p>



1. 별점, 발색력, 지속력, 수분감만 DataFrame



```python
result_1 = df[["별점","발색력","지속력","수분감"]]
result_1
```

```html
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>별점</th>
      <th>발색력</th>
      <th>지속력</th>
      <th>수분감</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>4</td>
      <td>보통이에요</td>
      <td>예상보다 짧아요</td>
      <td>보통이에요</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5</td>
      <td>아주 만족해요</td>
      <td>지속이 오래돼요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>2</th>
      <td>5</td>
      <td>아주 만족해요</td>
      <td>지속이 오래돼요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5</td>
      <td>아주 만족해요</td>
      <td>보통이에요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>523</th>
      <td>5</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
    </tr>
    <tr>
      <th>524</th>
      <td>5</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
    </tr>
    <tr>
      <th>525</th>
      <td>5</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>526</th>
      <td>5</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
    </tr>
    <tr>
      <th>527</th>
      <td>4</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
    </tr>
  </tbody>
</table>
<p>528 rows × 4 columns</p>
```



1\) 별점 오름차순 정렬



```python
df=result_1.sort_values(by="별점",ascending = True)
df
```

```html
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>별점</th>
      <th>발색력</th>
      <th>지속력</th>
      <th>수분감</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>365</th>
      <td>1</td>
      <td>아주 만족해요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
    </tr>
    <tr>
      <th>312</th>
      <td>1</td>
      <td>다소 아쉬워요</td>
      <td>예상보다 짧아요</td>
      <td>매트해요</td>
    </tr>
    <tr>
      <th>53</th>
      <td>1</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
    </tr>
    <tr>
      <th>58</th>
      <td>1</td>
      <td>다소 아쉬워요</td>
      <td>예상보다 짧아요</td>
      <td>매트해요</td>
    </tr>
    <tr>
      <th>507</th>
      <td>1</td>
      <td>다소 아쉬워요</td>
      <td>보통이에요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>245</th>
      <td>5</td>
      <td>아주 만족해요</td>
      <td>지속이 오래돼요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>244</th>
      <td>5</td>
      <td>아주 만족해요</td>
      <td>지속이 오래돼요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>243</th>
      <td>5</td>
      <td>아주 만족해요</td>
      <td>지속이 오래돼요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>253</th>
      <td>5</td>
      <td>아주 만족해요</td>
      <td>지속이 오래돼요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>263</th>
      <td>5</td>
      <td>아주 만족해요</td>
      <td>지속이 오래돼요</td>
      <td>아주 촉촉해요</td>
    </tr>
  </tbody>
</table>
<p>528 rows × 4 columns</p>
```



2\) 발색력, 지속력, 수분감 수치화


