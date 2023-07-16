# Python의 기초 03

> 20230703 멀티 캠퍼스 데이터 엔지니어링 교육. 왕기초
>
> > 20230703 수강
> >
> > 20230716 작성 시작

<br>
<br>

## 제어문(Control Statement)

> Python의 제어(출력, if문, for문 등등등등) 를 위해 사용하는 함수들.
>
> Python은 C 와 다르게 문장을 `;` 로 끝맺지는 않으나, 몇 몇 함수는 `:` 로 끝맺기 때문에 많이 유의할 것.
>
> 또한 들여쓰기(tab, Indentation) 를 생각없이 쓰지 말자. 함수에 영향을 미친다.
>
> 잘 기억하자 제발

<br>
<br>

## 1. 조건문(if ~ else)

> C와 용법이 유사

<br>

### 1-1) if

- 조건문 뒤에 콜론(`:`) 을 붙인다.
- 들여쓰기(tab, Indentation) 생각없이 쓰지 않기

<br>

### 1-2) if ~ else

### 1-3) if ~ elif ~ else

- 사용자 입력(`input()`)
- if 중첩 (else 안에 사용 가능)
- elif 적용. 철자 주의

<br>
<br>

## 2. 반복문(for ~ in)

> C와 용법이 유사

### 2-1) for ~ in with range()

- **range(`Start`, `Stop`, `Step`)**

> range(`Start`, `Stop`, `Step`) 함수에서 `Start`, `Step` 은 생략이 가능함
>
> 단, range 함수로 생성한 값은 List 가 아니라 range 객체로 반환 되는 것임.
>
> 따라서 필요에 따라 List 생성을 할 수 있다.

> 반복문을 사용할 때 
>
> 1. 특정 횟수 만큼 반복하거나
> 2. 숫자의 범위를 지정할 때
>
> 유용한 사용이 가능함.

### 2-2) for ~ in with List _ 1

> 한 줄로 List 의 값을 하나 하나 출력할 수 있다.(편하다)

### 2-3) for ~ in with List _ 2

> List 안의 List 도 출력할 수 있다.

### 2-4) for ~ in with if ~ else

> for 문과 if 문의 결합.



- enumerate(List)

> enumerate : 열거하다.

> 순서가 있는 자료형(List, Tuple, String) 의 값을 인덱스와 함께 열거.



### 2-5) for ~ in with break

- **break** 

> 반복문 종료



### 2-6) for ~ in with continue

- **continue**

> 반복문의 처음으로 돌아간다.
>
> 끝나는 것과는 다른게, 그 순서를 건너뛰는 개념으로 이해해도 무방.
