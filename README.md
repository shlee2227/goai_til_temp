# goai_til_temp
velog 서버 문제로 임시 TIL 작성

# set 세트
## 세트의 개념 
> 여러 데이터가 순서없이 저장되어있는 자료형 
> 순서가 없으므로 중복값이 허용되지 않음
## crud
### c
> {} 기호를 사용하여 생성 
```python
items = {"item1", "item2", "item3"}
print (type(items),items)
#
#결과
<class 'set'> {'item2', 'item3', 'item1'}
```

> set()함수로 생성
```python
items = set([1,2,3])
print (items)
#
# 결과
{1, 2, 3}
```

> 빈세트 생성
- new_set={}하면 같은 괄호쓰는 dict타입이 생성되어버림 
```python
my_dict = {}
print (my_dict, type(my_dict))
#
# 결과
{} <class 'dict'>
```

- set()함수 사용
```python
my_set = set()
print (my_set, type(my_set))
#
# 결과
set() <class 'set'>
```

- 중복값을 입력하면 알아서 예외처리
```python
nums = {1,2,2,3,1,2,3,1,2}
print(nums)
#
# 결과
{1, 2, 3}
```


### r
> index로 요소를 받아올 수 없음 (순서가 없으므로)


```python
items = {1,2,3}
print(items[0])
#
# 결과
TypeError: 'set' object is not subscriptable
```


### u
> 요소 추가 
- set.add(추가할 요소)
```python
my_set = {1,2,3,4,5}
my_set.add(6)
print (my_set)
#
# 결과
{1, 2, 3, 4, 5, 6}
```

> 요소 추가 
- set.update(추가할 요소 1, 2, 3...)
  - 순서가 없기 때문에 List처럼 위치 지정이 필요없음 
```python
my_set = {0, 1, 2, 3, 4}
my_set.update({4, 5, 6})
print(my_set)
#
# 결과
{0, 1, 2, 3, 4, 5, 6}
```

### d
> 요소 삭제
- set.remove(제거할 요소)
  - 하나의 값만 지울 수 있음 
  - 존재하지 않는 요소를 삭제하려 하면 에러 발생 
```python
my_set = {1,2,3,4,5}
my_set.remove(5)
print (my_set)
#
# 결과
{1, 2, 3, 4}
```
```python
my_set = {1,2,3,4,5}
my_set.remove(6)
#
# 결과
KeyError: 6
```

- set.discard(제거할 요소)
  - 존재하지 않는 요소를 지우려 해도 에러를 발생시키지 않음
 ```python
my_set = {1,2,3,4,5}
my_set.discard(6)
print(my_set)
#
# 결과
{1,2,3,4,5}
```
>전체 요소 삭제
- ser.clear()
```python
my_set = {1,2,3,4,5}
print(my_set)
my_set.clear()
print(my_set)
#
# 결과
{1,2,3,4,5}
set() # 빈 세트가 남음
```
- 세트 자체를 메모리에서 지우려면 del 사용
```python
my_set = {1,2,3,4,5}
del my_set
print (my_set)
#
# 결과
NameError: name 'my_set' is not defined
# 해당 변수가 정의되지 않았다고 오류 뜸 
```

## 집합연산
### 합집합
> 두 세트의 중복되는 원소를 제거하고 합한 세트를 리턴 
- set.union(set1, set2)
- set1.union(set2)
- set1 | set2
### 교집합
> 두 세트에 공통으로 포함된 요소만을 포함한 세트를 리턴 
- set.intersection(set1, set2)
- set1.intersection(set2)
- set1 & set2
### 차집합
> 한 세트의 요소에서 다른 세트에 포함된 원소를 제거하고 리턴
> 앞에오는 세트를 기준으로 함 
- set.difference(set1, set2)
- set1.difference(set2)
- set1 - set2




# dictionary 딕셔너리 
## 딕셔너리의 개념 
> {key:value} 형태의 자료구조
> key 값을 통해 value값 조회 가능
## crud
### c
> 생성
- new_dict = {key:value}

> key, value로 사용가능한 자료형
- 딕셔너리의 value에는 아무 자료형이나 들어갈 수 있으나 key에는 변경 불가능(immutable)한 값만 들어갈 수 있다. 

#가능한 key 값 
```python
my_dict2 = {
    4: 'four',
    1.5: 'one point five',
    'string_key': 'string_value',
    True: 'True',
    (1,4): 'tuple',
    # [1, 2, 3]: 'a list', # 리스트는 key로 사용 불가 
    # {10: 'ten'}: 'a dictionary' # dict은 key로 사용 불가 
}
```

#### 참고 변경가능(mutable)/변경 불가능(immutable)
# mutable, immutable

#int
a = 1
print(id(a))
print(type(a))
a = 2
print(id(a))
# 값만 바뀌었으니까 주소가 그대로일것 같지만 이렇게 주소가 바뀜 -> immutable
# a위치에 2가 들어가는게 아니라 2를 객체로 메모리에 넣고 a는 그 값을 레퍼런스 하는것!!!
b=2
print(id(b))

#list
a=[1,2,3]
print(a)
print(id(a))
a[2]=4
print(a)
print(id(a)) #요소가 바뀌었음에도 메모리 주소가 그대로인걸 확인 할 수 있음 -> mutable


```python
# 가능한 value 값
my_dict1 = {
    'key_1': 'first_value', 
    'key_2': 2,
    'key_3': 3.14,
    'key_4': True,
    'key_5': [4, 2, 1],
    'key_6': {'inner_key': 6} # 다중 딕셔너리
}
```

### r
> dict[key]: key에 해당하는 value 리턴

> dict.keys(): 딕셔너리의 모든 key 값을 리턴 
> dict.value(): 딕셔너리의 모든 vlaue 값을 리턴 
-.key(), .value를 쓴다고 해당 값을 리스트로 만들어서 메모리에 올리는 것은 아님 (리턴만 함)

> 특정 key를 가지는지 확인
- 찾는값 in dict : 찾는 key가 dict에 있는지 boolean 값으로 리턴
- dict.get(찾는값) : 찾는 key에 해당하는 value를 리턴, 없는경우 None을 리턴

> 길이 구하기
-  len(dict)

> 다중 딕셔너리
```python
game = {
"game1": {
    "title":"hello",
    "genre":"FPS",
    "year":1234
},
"game2" : {
    "title":"hello2",
    "genre":"FPS2",
    "year":12342
},
}
#game1의 자료형
print(type(game["game1"]))
#game2의 genre에 접근
print(game["game2"]["genre"])
#
# 결과
<class 'dict'>
FPS2
```

### u
> 항목 추가
- dict[new_key] = new_value
#기존 항목이 있으면 해당 key의 value 값 변경
- dict[key] = new_value

### d
> 항목 제거
- del dict[key]
- dict.pop(key)를 사용하면 원본 dict에서 key에 해당하는 value를 제거하고 제거한 값을 리턴함
