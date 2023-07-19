# Python_데이터 전처리 기초 07

> 20230707 멀티 캠퍼스 데이터 엔지니어링 교육. 왕기초
>
> 안까먹도록 잘 적어두자.
>
> 데이터 전처리 의 왕기초들을 배운다
>
> > 20230707수강
> >
> > 20230717 작성 시작 초안

<br>
<br>

## Data Preprocessing (데이터 전처리)

> 왕 큰 데이터 프레임 중 쓸모있거나 없는 것들을 정리하는 것.
>
> 왕 중요하다.

### **데이터 전처리 과정**

- 1. 데이터 프레임을 불러온다.
  2. 데이터 프레임을 확인한다.(특징을 확인한다)
     1. 우선 `.info()`  등을 이용해 데이터의 특징을 대략적으로 파악한다.
     2. 이 때 결측치가 존재하는지 확인한다.
     3. `head()` , `tail()` 함수로 진짜 어떻게 생겼는지, 결측치는 없는지 확인한다.
     4. 결측치가 존재한다면 다음 번호로, 없다면 큰 3번으로
     5. 결측치가 있으니 어떻게 처리할지 고민한다.
        1. 만약 양이 적거나 무의미하게 있다면 삭제한다.
        2. 양이 생각보다 많거나 유의미 하다면 대체값을 채운다.
        3. 결측치 대처방법을 명시한다.
  3. 데이터의 기본 통계정보 등을 확인하며 필요한 정보를 추출한다.



<br>
<br>

## 1. Missing Value

> Missing Value = 결측치
>
> 있어야 하는데 사실은 없는 것. -> 정상적인 계산 결과를 도출할 수 없다.
>
> 부르는 이름이 다양한데, 같은 파이썬 패키지 내부에서도 중구난방이니 그냥 알아두자.
>
> - NAN
> - NA
> - '    ' - 그냥 빈 공간
> - Null



### 1-1) 데이터 셋 불러오기

> 예제를 위해 샘플 데이터 셋을 불러온다.
>
> 이 경우 Seaborn에 내장된 'titanic' 데이터 셋을 활용한다.

```python
import seaborn as sns
TD = sns.load_dataset('titanic')
```

. seaborn 은 주로 sns로 줄인다.

- 데이터 셋 확인

```python
TD.info()
```



### 1-2) 결측치 확인

- 특정 열(Column) 에서 **결측치 확인**

```python
TD.head(10)
```

> 5번 행 'age' 열 결측치 존재



- **.value_counts(dropna = False)**

> dropna = drop nan = 결측치를 빼고 셀까요?
>
> True = 결측치 빼고 세줘
>
> False = 결측치 포함 세줘

```python
TD['deck'].value_count(dropna = False)
```

> 데이터 셋 'deck' 열 결측치 688개 존재.
>
> 891개 값 중 688개가 결측치..



- **.isnull()**

> is null? = null 인가요?
>
> 결측치 여부에 따라 출력 결과가 달라진다.
>
> True = 결측치 0
>
> False = 결측치 X

```python
TD.head(10).isnull()
```

> 맨 위 10줄 중 결측치로 인식되는 것은 True 로 출력




- **.isnull().sum(axis = 0/1)**

> axis = 0 = 의미-Index = 연산-Index를 기준으로 Column 을 계산한다.
>
> axis = 1 - Column

```python
TD.isnull().sum(axis = 0)
```

> 각 행의 결측치의 갯수를 합한다.





- **.notnull()**

> not null = null 이 아닙니다.
>
> 결측치 여부에 따라 출력 결과가 달라진다.
>
> True = 결측치 X
>
> False = 결측치 O

```python
TD.notnull()
```



- **그래프**를 사용하기



### 1-3) 결측치 삭제

> 결측치의 갯수가 결과에 영향을 미치 않을 정도로 적거나 결측치 존재가 무의미 할 때 삭제한다.

**1.**

```python
TD.dropna(thresh = 300, axis = 1).shape
```

> result : (891, 15) -> (891, 14)

> **dropna**
>
> drop + na
>
> 결측치 삭제 함수.
>
> 기준값 과 기준 축으로 설정한다.

> **thresh**
>
> 기준값. 역치의 기준.
>
> `thresh = x` 로 x에 정수를 기입해
>
> **결측치를 뺀 값(정상값)** 이 X개 이하면 `dropna` 를 활성화한다.

> **설명**
>
> 결국 열(axis = 1 = column) 들에서 정상값이  X개(thresh = x) 이하면 결측치를 삭제(dropna) 한 후, 모양새를 보이라는 코드이다. 

**2.**

```python
TD.dropna(subset = ['age'], how = 'any', axis = 0).shape
```

> result (891, 15) -> (714, 15)

> **subset = ['x']**
>
> 행(Index) 중에서 'x' 행에 결측치가 있는지 확인.
>
> 위 코드에서는 각 행들(Index = 891) 에서 열(columns = 15) 'age' 에 na 가 있는지 확인하는것

>  **how**
>
> any = 결측치가 존재만 한다면
>
> all = 'age' 외에도 모두 결측치라면

> **설명**
>
> 결국 행(Index = 891) 들을 기준으로 'age' 열에 결측치가 있다면 (subset = '[age]' , how = any ) 그 행 자체를 삭제한다(dropna)



### 1-4) 결측치 치환

> 결측치의 갯수가 결과에 영향을 미칠 정도로 많다면 기존의 Volum 값으로 치환한다.



- **연속형 데이터 치환**
  - **평균값으로 치환**

```python
TD['age'].fillna(int(TD['age'].mean(axis = 0)), inplace = True)
```

>**fillna**
>
>fill + na
>
>결측치를 뒤에 오는 값으로 채운다.

> `int(TD['age'].mean(axis = 0))`
>
> age 열의 평균을 낸다.

> **inplace = True / False**
>
> 값을 대체한다, 안한다.

> **코드해석**
>
> 데이터 프레임 TD 의 'age' 열들의 결측치를 'age' 열의 평균으로 대체한다.



- **명목형 데이터 치환**
  - **최빈값으로 치환**

```python
most_freq = TD['embark_town'].value_count(dropna = True).idxmax()

TD['embark_town'].fillna(most_freq, inplace = True)
```

> **.idxmax()**
>
> 명목형에서 제일 빈도가 높은 것을 출력.
>
> `.value_count()` 와 함께 사용



- **결측치 치환**
  - **앞, 뒤의 데이터 포인트로 치환**
    - `ffill` = front + fill
    - `bfill` = backword + fill



## 2. Filtering

> 주로 Index 단위로 이루어짐.



### 2-1) 데이터 셋 불러오기

### 2-2) 하나의 Index에서 범위 지정(이상 그리고 미만)

### 2-3) 하나의 Index에서 범위 지정(미만 또는 이상)

### 2-4) 두 개 이상의 Index에서 범위 지정

### 2-5) 특정 수를 포함



## 3. 데이터 프레임 합치기

> 여러가지 방법이 있는데 우리가 쉽게 생각하던 것 처럼은 아니다.
>
> 고민해보자



### 3-1) .concat()

> concat = 연결
>
> 축을 기준으로 블럭 붙이듯 붙여버린다.



### 3-2) .merge()

> merge = 병합
>
> 공통 된 데이터 index를 기준으로 두 개 이상의 데이터프레임을 병합(융합) 한다.



## 4. 그룹 연산

> 하나의 데이터 프레임에서 Serise 를 기준으로 DF을 재구성.(?)

### 4-1) .groupby() - 하나의 열 기준

### 4-2) .groupby() - 두 개 이상의 열 기준

### 4-3) .agg() - 함수 묶기

> Aggregation = 묶는다.
>
> 여러개의 **함수**를 groupby의 객체로 적용



### 4-4) .filter()

> 데이터 거르기
>
> `lambda` 를 활용한다.



## 5. pivot_table()

