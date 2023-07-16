# Python의 기초 02

> 20230703 멀티 캠퍼스 데이터 엔지니어링 교육
>
> > 20230703 수강
> >
> > 20230716 작성 시작

<br>

## Python Data Structure

> Python의 데이터 구조에 관련된 기초 함수들
>
> 주로 여러가지가 묶여 있는 모양새

<br>

## 1. String

> Structured. 정형적 구조.
>
> 글자(A), 문자(Apple) 등을 포함한다.



- 문자열(String) 생성

```python
S1 = 'The truth is out there.'
print(S1)
```

>result
>
>The truth is out there.

<br>

### 1-1) Concatenation

> Concatenation : 연결
>
> 문자 그대로 String 을 연결한다.

<br>

- `+` 문자열 **연결**
- `*` 문자열 **반복**

```python
print('=' * 40)
print('\t', S1)
print('=' * 40)
```

> result
>
> ========================================  
>
> ​			The truth is out there. 
>
> ========================================
> <br>
> 원래는 이쁘게 나왔는데 화면에 따라 계속 깨지는듯..

> **참고**
>
> `\t` 는 Escape Sequence(탈출 시퀀스) 중 하나로 tab(탭) 을 의미한다.
>
> 사용하면 사용 된 위치부터 `tab` 을 누른 것 마냥 뒤 문장이 후퇴한다.

<br>

**새로운 String 선언**

```python
S2 = 'The truth is'
S3 = ' out there.'
```



 **String 끼리 더하기**

``` python
S2 + S3
```

> result :
> The truth is out there.



**String 곱하기 (문자 열이라 반복을 의미)**

```python
S2 * 3
```

> result
>
> The truth isThe truth isThe truth is

```python
S3 * 3
```

>result
>
> out there. out there. out there.

<br>

### 1-2) Length

> String 의 크기(길이) 를 확인한다.
>
> len() 함수는 이후 Tuple, Dictionary 에서 요소 혹은 key 의 갯수를 확인할 때에도 사용된다. 
>
> 기억할것

```python
len(S1)
```

> result
>
> 23

<br>

### 1-3) Indexing

> 줄줄이 늘어있는 String 에서 주소를 확인하고 접근할 때 사용한다. 
>
> 포인팅의 기능도 겸한다.
>
> Indexing 의 개념은 이후 List, Tuple 등에서 사용하기도 한다.
>
> Dictionary는 순서가 없기 때문에 사용법이 다르다.

![인덱싱 샘플](C:\Users\KIM.E.C\AppData\Roaming\Typora\typora-user-images\image-20230716233146794.png)

```python
print(S1)
```

> result : The truth is out there.

```python
S1[1]
```

> result : 'h'

```python
S1[-13]
```

> result : 'i'

<br>

### 1-4) Slicing

> 정형적 구조(String, List, Tuple) 에서 특정 범위 연속된 주소를 추출할 때 사용한다.
>
> 새로 지정해서 주어진 데이터의 일부분을 새로운 시퀀스로 지정할 수 있다.

```python
print(S1)
```

> result : The truth is out there.

```python
S1[4] + S1[5] + S1[6] + S1[7] + S1[8]
```

> result : 'truth'



- **with Slicing**

> S1 [이상 : **미만**]

```python
S1[4:9]
```

> result : 'truth'

```python
S1[-19:-14]
```

> result : 'truth'

```python
S1[: 12]
```

> result : 'The truth is'

```python
S1[13 :]
```

> result : 'out there.'

<br>

### 1-5)  Formatting

> C언어에서 printf() 혹은 scanf() 안에 변수를 넣는 것과 유사한 것.
>
> 사용방법도 유사하나 2개 이상을 대입할 때엔 다르기 때문에 유의할 것.
>
> 그 외에 정렬 등으로도 사용이 가능하다.

- '%s' : String

```python
'The X-Files is an American science fiction %s.' % 'Drama'
```

> result : 'The X-Files is an American science fiction Drama.'



- 우측 정렬

```python
'%7s' % 'Drama'
```

> result :'   Drama'



- 좌측 정렬

```python
'%-7s' % 'Drama'
```

> result : 'Drama  '



- 2개 값 대입

```python
String = 'Drama'
Integer = 202

'The X-Files is an American science fiction %s, with %d episodes.' % (String, Integer)
```

> result : 'The X-Files is an American science fiction Drama, with 202 episodes.'

<br>
<br>

## 2. List

> Python 에서는 '배열'을 의미한다.
>
> List 의 값은 언제든지 변경이 가능하다.

<br>

### 2-1) `[]` 기호로 생성 - 값 변경 가능



- int 만 들어있는 List

```python
L1 = [1, 3, 5, 7, 9]
print(L1)
```

> result : [1, 3, 5, 7, 9]

```python
print(type(L1))
print(type(L1[0]))
```

> result :  <class 'list'> <class 'int'>

<br>

- str 만 들어있는 List

```python
L2 = ['HP', 'IBM', 'DELL', 'EMC', 'MS']
print(L2)
```

> result : ['HP', 'IBM', 'DELL', 'EMC', 'MS']

```python
print(type(L2))
print(type(L2[0]))
```

> result : <class 'list'> <class 'str'>

<br>

- int, str 혼합 List

```python
L3 = [1, '삼', 5, '칠', 9]
print(L3)
```

> result :

```python
print(type(L3))
print(type(L3[0]))
print(type(L3[1]))
```

> result : <class 'list'> <class 'int'> <class 'str'>

<br>

- List 안의 List

```python
L4 = [1, 3, ['HP', 'MS']]
print(L4)
```

> result : [1, 3, ['HP', 'MS']]

```python
print(type(L4))
print(type(L4[1]))
print(type(L4[2]))
print(type(L4[2][0]))
```

> result : <class 'list'> <class 'int'> <class 'list'> <class 'str'>

<br>

- List 안의 Tuple

```python
L5 = [5, 7, ('IBM', 'EMC')]
print(L5)
```

> result : [5, 7, ('IBM', 'EMC')]

```python
print(type(L5))
print(type(L5[1]))
print(type(L5[2]))
print(type(L5[2][0]))
```

> result : <class 'list'> <class 'int'> <class 'tuple'> <class 'str'>



### 2-2) Inexing

### 2-3) Slicing

### 2-4) Change Values

> List의 내용은 지정을 통해 변경 가능하다.

### 2-5) Delete Values

### 2-6) Function()

> sort 함수를 이용해 정렬 가능하다.

### 2-7) Operators

> List 의 내용을 병합, 반복이 가능하다.
>
> 단, 기본적으로 일반 산술연산은 사용이 어렵다.

<br>
<br>

## 3. Tulpe

### 3-1) `()` 기호로 생성 - 값 변경 불가능

### 3-2) Tuple in Tuple

### 3-3) List in Tuple

> Tuple 안의 List 는 값 변경이 가능하다.

<br>
<br>

## 4. Dictionary

> Unstructured : 비정형적 구조.
>
> 내용물의 순서가 존재하지 않고, Key - Value 구조를 이용해 값을 입출한다.
>
> Key 를 호출해 Value 를 불러온다.
>
> KVS (Key Value Store) 라고도 한다.
>
> `{}` 를 이용한다.

### 4-1) {Key:Value} 구조 선언

> { !!!(Key) : !!!(Value)} 로 `:` 앞에 오는 것이 Key, 뒤에 오는 것이 Value 이다.

### 4-2) Key:Value 추가

### 4-3) Key:Value 삭제

### 4-4) Function()

### 4-5) Dictionary with List

```python
L1 = ['Red', 'Green', 'Blue']
L2 = [255, 127, 63]
```

```python
D2 = {x : y for x, y in zip(L1, L2)}
print(D2)
```

>result
>
>{'Red': 255, 'Green': 127, 'Blue': 63}

> **코드 해석**
>
> D2 는 for 문을 활용한 Tuple 구조이다. `{}`
>
> x : y for x, y in zip(L1, L2)
>
> > for 앞에서 `x : y` 로 
> >
> > `x` 위치에는 Key 가 선언
> >
> > `y` 위치에는 Value 가 선언되었다.
>
> > for 뒤의 `x, y in zip(L1, L2)`
> >
> > 각각의 `x`, `y` 에는 어떤 것이 들어가는지를 선언하는데
> >
> > `x` - L1
> >
> > `y` - L2
>
> > `for ~ in ` 를 사용해 매칭 된 L1과 L2 를 반복한다.
>
> > > > `zip()` 함수는 ***같은 길이를 가진*** List, Tuple 등을 병렬 반복 작업을 수행하도록 묶는 함수이다.
> > > >
> > > > A = [1, 2, 3]
> > > >
> > > > B = [4, 5, 6]
> > > >
> > > > C = zip(A, B)
> > > >
> > > > result : C = [(1, 4), (2, 5), (3, 6)]
>
> > 결과적으로 L1 을 Key 로, L2 를 Value로 지정하되, List 가 통째로 매칭되는 것이 아닌, List 의 값들이 매칭된다.
> >
> > 따라서 코드의 결과는
> >
> > { `L1[0] : L2[0]` , `L1[1] : L2[1]` , `L1[2] : L2[2]` } 
> >
> > 가 되었다.



## 5. Casting

> 변수의 데이터 타입을 다른 타입으로 변경하는 것.
>
> ex) int -> float
>
> ex) List -> Tuple

### 1) Data Type

### 2) Data Structure



