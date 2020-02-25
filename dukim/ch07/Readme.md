# Chapter 7_제너레이터 사용하기
* 목표
    - 프로그램의 성능을 향상시키는 제너레이터 만들기
    - 이터레이터가 파이썬에 어떻게 완전히 통합되었는지 확인
    - 이터레이션 문제를 이상적으로 해결하는 방법
    - 제니레이터가 어떻게 코루틴과 비동기 프로그래밍의 기반이 되는 역할을 하는지 확인
    - 코루틴을 지원하기 위한 yield from, await, async def와 같은 문법의 세부 기능 확인
### 기술적 요구사항
### 제너레이터 만들기
* 한 번에 하나씩 구성요소를 반환해주는 이터러블을 생성해주는 객체
    - 메모리를 절약하는 것이 목적
#### 제너레이터 개요
* yield 키워드를 사용하면 제너레이터 함수가 됨
* 모든 제너레이터 객체는 이터러블임
* [제너레이터 적용 전/후 예제](generators_1.py)
    ``` 
    def _load_purchases(filename):
        purchases = []
        with open(filename) as f:
            for line in f:
                *_, price_raw = line.partition(",")
                purchases.append(float(price_raw))
        return purchases
    ``` 
    ```
    def load_purchases(filename):
        with open(filename) as f:
            for line in f:
                *_, price_raw = line.partition(",")
                yield float(price_raw)
    ```
#### 제너레이터 표현식
* 제너레이터를 사용하면 메모리 절약 가능
* 이터러블이나 컨테이너의 대안이 될 수 있음
* 컴프리헨션(comprehension)에 의해 정의될 수 있음
    - 컴프리헨션이란 이터러블 객체를 쉽게 생성하기 위한 기법
    - ex) ```lc = [i for i in rang(10)]```
###이상적인 반복
#### 관용적인 반복 코드
##### next() 함수
##### 제너레이터 사용하기
##### itertools
##### 이터레이터를 사용한 코드 간소화
#### 파이썬의 이터레이터 패턴
##### 이터레이션 인터페이스
#####이터러블이 가능한 시퀀스 객체
### 코루틴(coroutine)
#### 제너레이터 인터페이스의 메서드
##### close()
##### ```throw(ex_type[, ex_value[, ex_traceback]])```
##### send(value)
#### 코루틴 고급 주제
##### 코루틴에서 값 반환하기
#### 작은 코루틴에 위임하기 - yield from 구문
##### 가장 간단한 yield from 사용 예
##### 서브 제너레이터에서 반환한 값 구하기
##### 서브 제너레이터와 데이터 송수신하기
### 비동기 프로그래밍