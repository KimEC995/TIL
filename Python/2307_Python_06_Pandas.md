# Python_NumPy 기초 06

> 20230703 멀티 캠퍼스 데이터 엔지니어링 교육. 왕기초
>
> Pandas(판다스) 의 왕기초들을 배운다
>
> > 20230706수강
> >
> > 20230717 작성 시작 초안

<br>
<br>

## Pandas(Python Data Analysis Library)

> - 글자 + 숫자 형태의 행렬을 읽기 쉽게 처리함
> - 

[Pandas 홈페이지][https://pandas.pydata.org]

<br>
<br>

## 1. Pandas - Data Frame

### 1-1) Pandas Package import ~ ad

### 1-2) .read_csv()

### 1-3) .to_csv()

### 1-4) .read_excel()

### 1-5) .to_excel()

### 1-6) Data Frame Information

- **.info()**

```python
DF1.info()
```

> result
>
> <class 'pandas.core.frame.DataFrame'> RangeIndex: 17 entries, 0 to 16 Data columns (total 8 columns): #   Column     Non-Null Count  Dtype   ---  ------     --------------  -----   0   Name       17 non-null     object  1   Gender     17 non-null     object  2   Age        17 non-null     int64   3   Grade      17 non-null     int64   4   Picture    17 non-null     object  5   BloodType  17 non-null     object  6   Height     17 non-null     float64 7   Weight     17 non-null     float64 dtypes: float64(2), int64(2), object(4) memory usage: 1.2+ KB

> 대충 위와 같은 형식.
>
> 자주쓰는 함수이니 기억할 것

> **사용하는 경우**
>
> 1. 데이터 프레임의 크기를 확인할 때
> 2. 결측치를 확인할 때



- **.index - 행의 정보**

```python
DF1.index
```

> result : RangeIndex(start=0, stop=17, step=1)

> 인덱스의 정보를 보여줌.



- **.columns - 열의 정보**
- **.values - Array**

```python
```

> result
>
> 너무 길어서 안씀.
>
> 요약하면 Value 값들을 전부 보여주는데 형식은 Array 임



### 1-7) Function

- **.head()**
  - `()` 에 수를 지정하지 않으면 기본 5로 입력됨

> 위에서부터 ~ 줄 보여줌



- **.tail()**
  - 위의 `.head()` 와 비슷함

> 밑에서부터 ~ 줄 보여줌



- **.sort_values()**

> 값 들을 정렬함. 기본값은 오름차순

```python
DF1.sort_values(by = 'Height', ascending = True).head()
```

> **해석**

> **ascending**
>
> '오름차순' 이라는 뜻.
>
> 기본적으로 생략 가능하고, True 이나
>
> **내림차순**을 원하면 'ascending = False' 를 작성하면 됨

> DF1의 데이터를 정렬하되, 정렬은 'Height' 를 기준으로 하겠다는 뜻.
>
> 또한 `.head()` 로 위의 5줄만 보여달라는 뜻.



- **.describe()**

> describe = 묘사하다
>
> 숫자 데이터 통계량 전부 보여달라는 함수

```python
DF1.describe()
```



### 1-8) Indexing & Slicing

#### 1-8-1) loc(Location)

> index를 기준으로 만든 주소.
>
> Lable 주소 라고도 함.
>
> index는 Num 같아 보여도 사실은 str(object)로 인식된다.
>
> 따라서 이전 Array 에서 인덱싱을 하면 이상~ 미만 이었지만
>
> DF.loc() 에서는 문자이기 때문에
>
> **이상 ~ 이하** 이니까 유의할 것



#### 1-8-2) iloc(Integer Location)

> 절대 주소.
>
> DF 상에선 안보이지만 사실 존재함.
>
> 0 부터 시작한다. Num 맞다.
>
> **이상 ~ 미만**



## 2. Pandas - Series

> Series : 데이터 테이블의 세로로 한 줄 . 1차원의 구조
>
> Series + Series + ..... -> DataFrame(Table)
>
> Index , column 도 가지고 있다.



### 2-1) Series from DataFrame

- DataFrame_Name['Column_Name']



### 2-2) Function

- **.count()**
- **.sum()**
- **.mean()**



### 2-3) Indexing & Slicing



#### 2-3-1) loc(Location)

#### 2-3-2) iloc(Inter Location)



## 3. Pandas - Visualization

> 그래프 그리기 인데... Github에 업로드 했을때 그림 포함시키는거 찾아보고 해야할듯..
>
> Pandas 도 쓰긴 하는데 Seaborn 을 더 사용한다고 한다.
>
> 사용도에 따라 다른듯?
>
> 주로 Series 를 사용함



### 3-1) 선 그래프



### 3-2) 막대 그래프



### 3-3) 히스토그램



### 3-4) 상자 그래프



### 3-5) 산점도



### 3-6) 파이 그래프


