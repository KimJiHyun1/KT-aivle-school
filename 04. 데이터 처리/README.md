# 데이터 처리 


## 교육 일자
2022년 8월 8일 ~ 9일<br/><br/>


## 목차  

### day 1 (Pandas)  
  * merge, concat  
  * 시간 데이터 : rolling, shift, diff   
  * 범주형 데이터 비교 : crosstab, heatmap(groupby or pivot)
  
### day 2 (Data Preprocessing) 
  * Feature Engineering : 기존 컬럼으로 분석에 필요한 새로운 컬럼 도출  
  * 결측값 처리 : isnull(), dropna(), fillna(), .interpolate()  
  * Dummy Variable (가변수화) : 범주형 데이터 > 0, 1 : pd.get_dummies()  
  * Scailing : MinMaxScaler, StandardScaler <br/><br/><br/>


## 요약  

### merge 
  * **pd.merge**(df1, df2, how=어떻게?, on=어떤 컬럼 기준?)
  * how : left(df1 고정 + df2), right(df2 고정 + df1), inner(서로 같은 것만), outer(전부 다)
  
### concat
  * **pd.concat**([df1, df2, ...], axis=행?열? 기준)
  * axis = 0 : 행 기준 (위아래로 붙이기)
  * axis = 1 : 열 기준 (옆으로 붙이기)
  
### rolling, shift
  * df['col'].**rolling(n)**.mean() : window size n의 평균값
    * n의 default = 1
    * .rolling() 뒤에 집계 연산 함수(mean(), max(), ...)를 써줘야 의미가 있다
    * .rolling(n, **min_period=1**) : window에 데이터가 최소 1개 이상 있으면 그것들의 평균값, 0 < **min_periods** <= window size
  * df['col'].**shift(n)**
    * 양수 : n칸만큼 내린다
    * 음수 : n칸만큼 올린다
  
### crosstab
  * **pd.crosstab**(행으로 쓸 컬럼, 열로 쓸 컬럼, normalize='옵션')
    * normalize : columns(열 기준 %), index(행 기준 %), all(전체 기준 %)
    
### heatmap
  * 두 범주 집계 시각화 : **sns**(**groupby한 df** or **pivot한 df**)
    * **pivot** : df.pivot(index, columns, values)
    * sns = import **seaborn** as **sns**
<br/><br/>
__ __ __ __ __ __ __
<br/>

### Feature Engineering
  * 원래 있던 컬럼들을 이용해 새로운 컬럼을 만들어내는 것
    * ex) 날짜 형식으로 변환(str > datetime) : **pd.to_datetime()**+.dt.month/year/week/weekday 등

### 결측값 처리
  * 결측값 확인 : df.**isnull()**.sum() : 컬럼별 결측값의 합계
  * 결측값 제거 : df.**dropna**(axis=0(행) or 1(열))
  * 결측값 교체 
    * df.**fillna**(채울 값, method='ffill' or 'bfill')
    * df.**interpolate**(method='linear') : 시계열 데이터라면, 앞 뒤 값의 중간값으로 채우기
    
 ### Dummy Variable (가변수화, one-hot encoding)
  * 범주형 데이터는 가변수화 해서 사용해야 한다 ex) 봄, 여름, 가을, 겨울
  * **pd.get_dummies**(df['col'], prefix = '', drop_first = True)
    * **prefix** : 접두어 : 만들어지는 컬럼 앞에 붙는 글자
    * **drop_first = True** : 가변수화 해서 생긴 컬럼 중 하나는 나머지 컬럼들에 의해 결정되므로 하나는 빼준다.
      * ex) 봄, 여름, 가을이 아니라면 겨울이므로 봄, 여름, 가을만 남기고 겨울은 삭제
    * 가변수화 한 뒤, 원래 데이터와 합친다 : pd.concat([원래 df, 가변수화한 df], axis = 1)
    
### Scailing
  * 값들의 범위가 제각각이니 범위를 통일시킨다
  * **MinMaxScaler** : 최솟값 0 ~ 최댓값 1
  * **StandardScaler** : 평균 0이면서 표준편차 1
  
