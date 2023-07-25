# Python_데이터 전처리 기초 08 - Multi-Index

> 멀티 캠퍼스 데이터 엔지니어링 교육. 왕기초
>Multi-Index

<br>
### Multi-Index

이름 그대로 인덱스가 다중으로 존재할 때의 상태를 지칭.
피벗 테이블이나 그룹화를 통해 생성되는 경우 이며, 이름이나 값을 재 지정할 수 있다.
<br>
## .xs()
- `.xs()` : Cross Section
> 멀티 인덱스 내부의 값을 특정할 수 있다.

### 단일
```python
TD.xs('First', level = 'class', axis = 0)
```
> 지난 번에 피벗테이블을 이용해 만든 멀티 인덱스의 값들 중 [객실 등급이 1등급] 인 값의 행[axis = 0] 을 출력한다.

### 다중
```python
TD.xs(('First', 'male'), level = ['class', 'sex'], axis = 0)
```
> [객실 등급이 1등급 이면서 성별은 남성] 인 경우.
> 인자는 `()` 리스트형
> Level 은 `[]` 튜플 형으로 분류

<br>
## set_names()
- `set_names()` : 라벨 재설정. 리스트
> ex)  TD의 열 값을 피벗 테이블로 재설정 하면 이름이 [None] 으로 나오는 경우가 있다. 이 때 [None] 의 라벨을 지정 값으로 바꾼다.

 ```python
 TD.columns.set_names(['Header', 'Function', 'Survived'], inplace = True)

TD.columns
```
<br>
## set_levels()
- `set_levels()` : 값을 바꿔준다. 리스트
level 을 지정할 수 있다.
> ex) TD의 열 중 특정 Level 에서의 값이 죽으면 0, 살면 1로 나온다.
> 알아보기 힘드니 0 == Dead ,  1 == Alive 로 바꿔주자.

 ```python
 TD.columns.set_levels(['Dead', 'Alive'], level = 2, inplace = True)

TD.columns
```

 <br>
