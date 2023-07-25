# Python_NumPy 기초 05

> 20230703 멀티 캠퍼스 데이터 엔지니어링 교육. 왕기초
>
> NumPy(넘파이) 의 왕기초들을 배운다
>
> > 20230706수강
> >
> > 20230717 작성 시작

<br>
<br>

## NumPy(Numerical Python)

> - 수학 및 과학적 연산을 Package 형태로 쉽고 빠르게 지원한다
> - 다차원 행렬(Tensor[Array, Matrix]) 을 처리
> - 일반적으로 같은 타입의 데이터 값들로 구성됨
>   - ex) int-int

[NumPy 홈페이지][[https://numpy.org]

<br>
<br>

## 1. NumPy Package import ~ as



## 2. Array 생성

> Array = 배열.
>



### 2-1) Scalar - 0D Array - Rank 0 Tensor

>0D 는 점이다.
>
>행렬에서 0D는 단 하나의 값만 List에 들어있는 것



### 2-2) Vector - 1D Array - Rank 1 Tensor

> 1D 는 선이다.
>
> 일렬로 주르륵 존재하는 것



### 2-3) Matrix - 2D Array - Rank 2 Tensor

> 2D 는 면이다.
>
> 보통 Table 이라고 부르는 모양새



### 2-4) Array - 3D Array - Rank 3 Tensor

> 3D 는 정육면체이다.
>
> 3차원 행렬로, (**축**,행,렬)이라 부른다.



## 3. 행렬 구성 확인 방법과 재구성

> 행렬이 어찌 생겨 먹었는지 확인하고 재구성할 수 있다.



### 3-1) .shape() 

> 행렬의 차원과 크기를 Tuple 형태로 나타낸다.



### 3-2) .ndim()

> 행렬의 차원을 표시한다



### 3-3) .size()

> 행렬의 원소의 개수를 나타낸다.



### 3-4) .reshape()

> 행렬의 크기를 재구성하여 새롭게 만든다.
>
> 이전의 행렬 자체를 수정하는거 아님. 새로 지정해야함



### 3-5) .flatten()

> 행렬을 납작하게 만든다.
>
> 즉, 행렬을 (1, x) 형태로 만든다.



## 4. 범위지정(arange()) 함수

> Array 형식 에서 사용이 가능하다.
>
> Array + .range() = .arange()
>
> `.range()` 와 용법이 유사하다.
>
> 생성 결과는 (1,X) 형식 이기 때문에 2D 이상을 만들고 싶으면 `.reshape()` 사용하기.



### 4-1) 연속된 10개의 값 생성

### 4-2) 1 부터 9까지 1 간격으로 생성

### 4-3) 1 부터 9 까지 2 간격으로 생성

### 4-4) Array 생성 후 .reshape() 적용

> 1D를 2,3..D 로 만듬.



## 5. 특별한 형태의 Array 생성



### 5-1) 0과 1로만 구성된 Array

> 0 이나 1로만 구성 된 Array를 만든 후, 산술연산을 활용해 특별한 수로만 이루어진 행렬 생성이 가능함.



### 5-2) 3 * 3 단위 행렬

>대각선 들만 1. 나머지는 0



### 5-3) 난수 Array 생성

> 랜덤(?) 한 숫자로 이루어진 Array 생성함.

- **실수 난수 생성**
- **주어진 정수 범위에서 난수 생성**
- **np.random.seed()**
  - 의사난수 생성 초기값 지정
  - **항상 같은 난수 생성**
  - 비복원 추출 -> 복원x
- **정규분포**
- **단일분포**

## 6. Array 연산

### 6-1) 기본 연산

- 각각의 행과 열의 값을 매칭하여 연산 수행
  - **크기가 같아야 가능하다!!**

### 6-2) 통계량 연산

> 생각보다 많이 쓴다...
>
> 기억할것

- **총 합**

```python
A1.sum()
```

> result : 419

> A1 의 Value 총 합.
>
> 단순 행 합뿐만 아니라 Value 들의 총 합이다.



- **평균**

```python
A2.mean()
```

> result : 90.4

> A2 Value 총 합 / A2 Value 갯수



- **분산**

  - 'ddof = 0'

  > ddof
  >
  > Delta Degrees Of Freedom
  >
  > **표준편차** 또는 **분산**의 자유도 조정을 의미. `0`, `1` 의 값을 지님.
  >
  > 0 : 편향 추정 -> 계산하는 대상이 모집단인 경우
  >
  > 1 : 비편향 추정 ->계산하는 대상이 표본집단인 경우
  >
  > 기본은 `0`으로 설정됨

```python
A2.var()
```

> result : 15.040000000001



- **표준 편차**
  - 'ddof = 0'

```python
A2.std()
```

> result : 3.8781....



- **최솟값**

> 

```python
A2.min()
```

> result : 85




- **각 열의 최솟값**
> axis  = 0 == 열 == column

```python
A3.min(axis = 0)
```

> result : array([85, 84, 75])



- **각 행의 최솟값**
> axis = 1 == 행 == index

```python
A3.min(axis = 1)
```

> result : array([75, 84, 80])

```python
A3.min(axis = 1, keepdim = True)
```

> result :
>
> array([[75],
>
> ​			[84],
>
> ​			[80]])

> **keepdim = True / False**
>
> keep dimention 으로 차원을 유지하라는 말.
>
> 즉, 모양새를 유지하라는 뜻
>
> 위 코드 같은 경우 각 행에서의 최솟값들을 뽑았으나, 행의 모양이 무너지고 하나의 열로 바뀌었다.
>
> 따라서 모양을 알기 힘드니 모양 유지하라는 뜻.
>
> 생략 가능하고 기본값은 `False` 다.



- **최댓값**
```python
A2.max()
```

> result : 97



- **누적 합**
> 누적 + 합
>
> cumulative + summary
>
> -> cumsum

```python
A1.cumsum()
```

> result :
>
> array([ 85, 178, 253, 350, 419])



- **누적 곱**
```python
A1.cumprod()
```

> result : 
>
> array([        85,       7905,     592875,   57508875, 3968112375])




## 7. Matrix 연산

### 7-1) Matrix 의 곱

### 7-2) 전치 행렬
