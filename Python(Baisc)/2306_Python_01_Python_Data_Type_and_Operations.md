# Python의 기초 01

> 20230630 멀티 캠퍼스 데이터 엔지니어링 교육 내용
>
> Colaboration Lab 을 활용
> > 20230630 수강 <br>
> > 20230712 작성시작



## Python Data Type and Operations

 - 시작하기 전 기타 경고 문장을 무시하는 코드 작성

   ```python
   import warnings
   # Warnings 항목을 불러온다.
   
   warnings.filterwarnings('ignore')
   # Warnings의 내용을 필터 후 ('무시한다')
   ```


## Python Function



### 1) 함수 실행

- **print() 실행**

```python
print('Hello World')
# colab이나 Jupyter Notebook 특성상 'print('-')' 를 작성하지 않아도 동작은 하지만, 다양한 프로그램 언어의 통일을 위해 이후 반드시 작성
```



- **매개변수(Parameter) 및 인자/인수(Argument) 지정**

> 매개변수(Parameter) -> 함수에서 정의되는 변수. 함수에 전달되는 값들을 저장하고 처리하는데 사용됨.
>
> 인자/인수(Argument) -> 함수를 호출할 때 전달되는 값. 매개변수에 할당되어 함수 내부에서 사용되거나 처리됨.

```python
print('HelloWord', end  = '\t')
```

위의 문장같은 경우 `HelloWorld` 가 인자(Argument), `\t` 가 들어가는 매개변수(Parameter)는 `end` 이다.



- **내장 매뉴얼**

```python
help(print)
```

> 내장 매뉴얼은 Python에서 기본 제공하는 매뉴얼로, 따로 패키지나 클래스를 인스톨하지 않아도 확인이 가능함.

<br>

### 2) 객체(Object) 선언

> 파이썬 식별자(Identifiers)는 객체, 함수, 클래스, 모듈 또는 다른 개체 식별에 사용되는 이름.

- 식별자는 문자(A - Z, a - z)로 시작하고 띄어쓰기 대신 밑줄(_), 숫자 (0 - 9)를 사용
- 특수문자 @, $, &는 식별자 사용 불가
- 파이썬은 대소문자를 구분한다.

```python
koo = 'Data Analytics'
print(koo)
```

> 결과 : 'Data Analytics'
>
> 이 경우
>
> koo == 변수로 사용되는 식별자



```python
type(koo)
```

> 결과 : str



- 예약어(35개)
  - 객체명(식별자)로 사용할 수 없음.

```python
import keyword
# 예약어 35개를 볼 수 있는 모듈

keyword.kwlist
# 'keyword'는 위쪽의 모듈, 'kwlist'는 모듈의 내용을 불러온,ㄴ 리스트
```

> 결과 : ['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
>
> 위 35개 단어는 예약어로 객체명(식별자)로 사용이 불가함.



## Python Data Type



### 1. Numeric

> 숫자, 수 등의 의미를 지님



- 정수

```python
print(888)
print(type(888))
```

> result 
>
> 888
>
> <class 'int'>



- 8진수

```python
print(0o77)
# 8진수는 Octal number 로 8진수를 표기할 때 앞에 숫자 `0`과 영문 소문자 `o`를 붙여 표기한다. 
print(type(0o77))
```

> result
>
> 63
>
>  <class 'int'>



- 16진수

```python
print(0xff)
# 16진수는 Hexadecimal number 로 16진수를 표기할 때에는 앞에 숫자 `0`과 영문 소문자 `x`를 붙여 표기한다.
# 16진수는 10진수 이상의 진법으로, 10부터 16까지를 표기할 때에는 영문 소문자 `a` 부터 `f`까지 대응해서 사용한다.
print(type(0xff))
```

> result
>
> 255
>
> <class 'int'>



- 2진수

```python
print(0b1001)
# 2진수는 Binary number 로 2진수를 표기할 때에는 앞에 숫자 `0`과 영문 소문자 `b`를 붙여 표기한다.
print(type(0b1001))
```

> result
>
> 9
>
> <class 'int'>

<br>

- 실수

```python
print(3.14)
print(type(3.14))
```

> result
>
> 3.14
>
> <class 'float'>

<br>

- 과학적 표기법

```python
print(5e-4)
print(type(5e-4))
```

> result
>
> 0.0005
>
> <class 'float'>

```python
print(5e + 4)
print(type(5e+4))
```

> result
>
> 50000.0
>
> <class 'float'>

<br>

- 복소수(Complex)

> 복소수(Complex)란 실수와 허수로 구성되는 수
>
> ex) 4 + 2j 에서 '4'는 실수 부분, '2j'는 허수부분

```python
print(8 + 9j)
print(type(8 + 9j))
```

> result
>
> (8 + 9j)
>
> <class 'complex'>

<br>

### 2. String

```py
print('A')
print(type('A'))
```

> result
>
> A
>
> <class 'str'>

```python
print('Data Analytics')
print(type('Data Analytics'))
```

> result
>
> Data Analytics
>
> <class 'str'>

<br>

### 3. Logical

<br>

- 참

```py
print(True)
print(type(True))
```

> result
>
> True
>
> <class 'bool'>

<br>

- 거짓

```python
print(False)
print(type(False))
```

> result
>
> False
>
> <class 'bool'>

<br>

## 산술연산(Arithmetic Operation)

### 1. 사칙연산
> 하단에서 보는 바와 같이 Python에서는 따로 명령어를 입력하지 않아도 간단한 사칙연산은 그냥 결과를 출력한다.

<br>

- 덧셈

```python
 8 + 9
```

> result
>
> 17

<br>

- 뺄셈

```python
8 - 9
```

> result
>
> -1

<br>

- 곱셈

```python
8 * 9
```

> result
>
> 72

<br>

- 실수 나눗셈

```python
10 / 3
```

> result
>
> 3.3333333333333335
> 17번째에서 올림.

<br>

- 나눗셈 후 몫 반환

```python
10 // 3
```

> result
>
> 3
> 나눗셈 후 몫만 정수형으로 반환함.
> 나머지는 몫 연산에 영향을 주지 않음.

<br>

- 나눗셈 후 나머지 반환

```python
10 % 3
```

> result
>
> 1
> 10에서 3을 나누고 남은 1만 반환.
> 10 / 3 의 나머지 0.333... 가 아님을 유의할것.

<br>

- 제곱

```python
9 ** 3
```

> result
>
> 729

```python
pow(9 , 2)
```

> result
>
> 81
> pow(Power) 는 수학적으로 '거듭제곱' 을 의미한다.

<br>

### 2. 절댓값

```python
abs(-3)
```
> result
>
> 3
> abs(Absolute Value) 는 수학적으로 절댓값을 의미한다.

<br>

### 3. 진법 변환

- 16진수로 변환

```python
hex(16)
```

> result
>
> 0x10
> Hexdecimal Number 의 줄임말 (hex) 를 사용한다.

- 8진수로 변환

```python
oct(8)
```

> result
>
> 0o10
> Octal Number 의 줄임말 (oct)를 사용한다.

- 2진수로 변환

```python
bin(9)
```

> result
>
> 0b1001
> Binery Number 의 줄임말 (bin)을 사용한다.

<br>

### 4. 반올림

- round(number, [digits])
> digits: 생략 가능. 
>
>어느 자리 숫자 + 1 에서 반올림 할지 설정한다. 
>
>없으면 소숫점 첫 번째 자리에서 반올림.

```python
round(24.47)
```

> result :
> 24

```python
round(24.57)
```

> result :
> 25

```python
round(24.57 , 0)
```

> result :
> 25.0

```python
round(24.57 , 1)
```

> result :
> 24.6

```python
round(24.57 , -1)
```

> result :
> 20.0

```python
round(25.47 , -1)
```

> result :
> 30.0

```python
round(25.478 , 2)
```

> result :
>25.48

## 비교연산(Comparison Operation)

### 1. Numeric



#### 2. Character

