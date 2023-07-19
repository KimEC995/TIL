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
> >
> > 20230718 내용 보강
> >
> > 20230719 내용 보강

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

```python
TD['embark_town'].fillna(method = 'ffill', inplace = True)
```





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

> 하나의 데이터를 그룹화 하여 그룹 별 연산을 수행.



### 4-1) .groupby() - 하나의 열 기준

```python
TD_G = TD.groupby(['class'])
```

> TD 데이터 셋의 열 'class' 를 기준으로 그룹화 한다.
>
> class에는 'First' , 'Second', 'Third' 의 3 가지 값이 있는데, 그것을 기준으로 하는 것.



### 4-2) .get_group() - 키 그룹 정보 확인

```python
TD_G.get_group('First')
```

> 이미 그룹화 된 그룹의 키 정보를 확인한다.
>
> 이 경우 'First' 그룹에 속해있는 데이터 셋을 출력한다.



### 4-3) for 문을 활용한 그룹 정보 확인

```python
for key in ['First', 'Second', 'Third']:
    print(TD_G.get_group(key).head(3))
    print('\n')
```

> 4-2의 `.get_group()` 를 3번 사용하기 번거로워 `for` 문을 활용하였다.



### 4-4) 그룹 통계 연산

```python
TD_G.mean()
```

> mean 뿐만 아니라 연산 모두 사용 가능하다.



### 4-5) .groupby() - 두개의 열 기준

```python
TD_G_02 = TD.groupby(['class', 'sex'])
```

> 두 줄 쓸 필요 없이 그냥 키를 두개 준다.
>
> 단, 각 각 다른 열 이어야함.



- **하나 확인 - .get_group()**

```python
TD_G_02.get_group(['First', 'Female'])
```



- **여러개 확인 - for 문 활용**

``` python
for key, group in TD_G_02:
    print('* key:' , key)
    print('* number:', len(group))
    print(group.head(3))
    print('\n')
```

> result. 요약
>
> \* key : ('First', 'female') 
>
> \* number : 94
>
> First, female  3줄
>
> \* key : ('First', 'male') 
>
> \* number : 122
>
> First, male  3줄
>
> .
>
> .



### 4-4) .agg() - 함수 묶기

> Aggregation = 묶는다.
>
> **여러개의 함수**를 groupby의 객체로 적용



- **.agg()**

```py
TD_G.agg(['std', 'mean'])
```



- **특정 열에만 적용**

```python
TD_G.age.agg(['min' , 'max'])
```



- **두 개의 열에 따로 적용**

```python
TD_G.agg({'age' : ['mean', 'std'], 'fare' : ['min', 'max']})
```

> 딕셔너리 `{}` 필수



### 4-5) .filter()

> 데이터 거르기
>
> 너무 길어져서 `lambda` 를 활용한다.



- **.filter(lambda x : )**

**1.**

```python
TD_G.filter(lambda x : len(x) >= 200).head()
```

> `lambda x : len(x) >= 200`
>
> 앞의 TD_G 의 그룹 들 중 데이터의 갯수가(len(x)) 200개 이상인 것들만 필터함
>
> 그룹 중 Second 는 184개의 데이터로 탈락한다.



**2.**

```python
TD_G.filter(lambda x : x['age'].mean() < 30).head()
```



- **.apply()**

```python
TD_G.apply(len)
```

> **.apply()**
>
> `()` 안에 len 외에도 다양한 함수를 넣을 수 있다.
>
> 각 그룹 별로 연산을 적용한다.

> **`.agg()` 와 `.apply()`** 의 차이
>
> `.agg()` 여러개의 함수를 **동시**에 적용. 주로 'mean', 'std' 구할때 씀
>
> `.apply()` 여러개의 함수를 **개별** 적용. 반드시 하나의 함수를 적용해야 함. 주로 'len' 을 씀



## 5. pivot_table()

> pivot - 고정해서
>
> table - 테이블로 재구성
>
> -> 하나의 원본 데이터 프레임을 쪼개고 재구성한다.



### 5-2) pivot_table() 구성 요소

- **Index**
- **columns**
- **values**
- **aggfunc** : Aggregation Function -> 적용 함수

```python
TD_1 = pd.pivot_table(TD,
                   index = 'class',
                   columns = 'sex',
                   values = 'age',
                   aggfunc = 'mean'
                   )
```

> 원본 데이터 프레임 TD에서 필요한 정보만 모인 테이블을 재구성
>
> 원래 열이었던 'class' 를 행으로 만들어
>
> 각 등급 별 남성과 여성의 나이 평균으로 이루어진 테이블이 된다.



### 5-3) 두 개의 적용 함수

```python
TD_2 = pd.pivot_table(TD,
                      index = 'class',
                      columns = 'sex',
                      values = 'age',
                      aggfunc = ['mean', 'sum']
                     )
```

> 적용 함수 'mean' 과 'sum' 두 가지로 만들었다.
>
> 다중컬럼으로 출력됨.



### 5-4) 다중 인덱스, 다중 데이터, 다중 함수

```python
TD_3 = pd.pivot_table(TD,
                     index = ['class', 'sex'],
                     columns = 'survived',
                     values = ['age', 'fare'],
                     aggfunc = {'age' : ['mean', 'std']
                               'fare' : ['max', 'min']}
                     )
```

> 객실 등급별 성별로 나뉘는 다중 인덱스
>
> 두 종류의 값이 들어가는 다중 데이터
>
> 각 값마다 다르게 적용되는 다중 함수까지 모였다.
>
> 주의점은 `index`, `columns`, `values` 를 여러 개 작성할 땐 `[]` (리스트)로 묶고
>
> `aggfunc` 를 묶을 땐 `{}` (딕셔너리)를 사용한다. -> 함수니까 

