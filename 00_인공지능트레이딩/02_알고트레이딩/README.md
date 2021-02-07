# 알고트레이딩 기본기 정리

## A. 주식 API, 거래소 정보 가져오기, 특정 기업 추적 및 종가흐름파악

### 1. 설치 및 로딩
```
pip install -U finance-datareader
import FinanceDataReader as fdr

df_krx = fdr.StockListing('KRX')
print(len(df_krx))
df_krx.head()
```

### 2. 주식시장 거래소 정보
```
# 한국
# 심볼	거래소
# KRX	KRX 종목 전체
# KOSPI	KOSPI 종목
# KOSDAQ	KOSDAQ 종목
# KONEX	KONEX 종목
# 미국
# 심볼	거래소
# NASDAQ	나스닥 종목
# NYSE	뉴욕 증권거래소 종목
# AMEX	AMEX 종목
# SP500	S&P 500 종목
```

### 3. 카카오 주식, 상장코드 추적 및 종가추이 가시화
```
a = df_krx[df_krx['Name'].isin(['카카오'])]['Symbol']
print(a)

df = df_krx[df_krx['Name'].isin(['카카오'])]
df.set_index('Symbol', inplace=True)
print(df)
print(df.index[0]) #005930

df_krx[df_krx['Symbol'].isin(['005930'])]

# 종가 추이 가시화
df = df_krx[df_krx['Name'].isin(['카카오'])]
df.set_index('Symbol', inplace=True)

df = fdr.DataReader(df.index[0],'2020')
df.head(10)
df['Close'].plot()
```
<br>
<hr>


## B. Pandas 사용법

### 1. 로딩
```
import pandas as pd
df = pd.read_csv('AAPL.csv')
print(type(df.index))      #<class 'pandas.core.indexes.range.RangeIndex'>
print(type(df.index[0])) # <class 'int'>
```

### 항목순회
```
for col in df.columns:
    series = df[col]
print(series) #마지막 항목: Name: Volume, Length: 9715, dtype: float64
```

### 2. index를 설정하여 로딩
```
df = pd.read_csv('AAPL.csv', index_col='Date', parse_dates=['Date'])
print(type(df.index)) # <class 'pandas.core.indexes.datetimes.DatetimeIndex'>
```

### 3. 결측치 확인/제거
```
import numpy as np 
print(df.isna().sum())
print(df.isin([np.nan, np.inf, -np.inf]).any(1))
df[df.isin([np.nan, np.inf, -np.inf]).any(1)]
# null 제거
df = df.dropna(axis=0) #0:row, 1:col
```

### 4. 슬라이싱/인덱싱/서브셋
```
#열단위 출력
print(df['Open'].head())
print(df[['Open','Close']].head()) # 2개 이상은 array로 넘거야함?
#row 단위, index조건 출력
print(df[0:3])
print(df['2018-10-01':'2018-10-05'])

#loc, iloc
print(df.loc['2018-10-01'])
print(df.iloc[0])

print(df.loc['2018-10-01':'2018-10-05', ['Open','Close']])
print(df.iloc[8000:8005, [0,1]])
```

###  5. 금융 시계열 분석에 유용한 pandas 함수
```
#shift: 원하는 시간 주기 간격만큼 index를  shift가능
df['Close_lag1'] = df['Close'].shift(1)

#가시화
df['Close'].asfreq('M',method='ffill').plot(legend=True)
shifted = df['Close'].asfreq('M',method='ffill').shift(10).plot(legend = True)
shifted.legend(['Close','Close_lagged'])

#percent change : 현재값과 이전값의 변화량을 백분위로 표현
df['pct_change'] = df['Close'].pct_change()
print(df.head(7))
df['pct_change'].plot()

#rolling: 이동 평균선
df = pd.read_csv('AAPL.csv', index_col='Date', parse_dates=['Date'])
df = df.loc['2018-01-01':'2018-12-31']
df['MA_5'] = df['Close'].rolling(window=5).mean()
df['MA_10'] = df['Close'].rolling(window=10).mean()
df['MA_20'] = df['Close'].rolling(window=20).mean()
df.head(10)

#https://rfriend.tistory.com/502
import matplotlib.pyplot as plt
plt.figure(figsize=(15, 10))
plt.plot(df.index, df.Close, 'y-', label='close')
plt.plot(df.index, df.MA_5, 'b-', label='MA')
plt.plot(df.index, df.MA_10, 'r-', label='sma_10d')
plt.plot(df.index, df.MA_20, 'g-', label='sma_20d')
plt.legend()
plt.show()
```
