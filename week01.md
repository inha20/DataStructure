https://github.com/inha20/VacationDataStructure/blob/main/01week.md






# OT
> 자료구조
<details><summary> 예시
</summary>
➜ 리스트<br>
➜ 그래프<br>
➜ 스택 ; // LIFO, FILO<br>
➜ 큐 ; // FIFO<br>
➜ 트리 ; <br>
➜ 선형, 비선형 ; <br>
➜ Soarting, Searching ; <br>
</details>



> 알고리즘


<details><summary>
조건
</summary>
➜ 0개 이상의 입력<br>
➜ 1개 이상의 출력<br>
➜ 각 명령어의 의미는 명확하고 명백해야 한다.<br>
➜ 한정된 횟수 후 반드시 종료되어야 하는 유한성.<br>
➜ 각 명령어들은 실행이 가능해야 하는 유효성.<br>
</details>

<details><summary>
기술방법
</summary>
➜ 자연어<br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 읽기 쉬움<br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 명확성 유지 위한 단어 정의 필요<br>
➜ 흐름도<br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 직관적, 이해 쉬움, <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 복잡한 알고리즘은 상당히 복잡해짐. 기술이 어려움.<br>
➜ 유사 코드 (슈도 코드)<br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 알고리즘의 핵심 내용에만 집중 가능. <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 세부 문법 등의 프로그램 구현시 문제점을 숨길 수도 있음.<br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ java의 세부 문법들이 이해를 방해.<br>
</details>




<details><summary>
추상 자료형
</summary>
➜ 피카소의 추상화처럼, 추상적이고 특징적인 부분만 묘사함. <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 데이터와 연산이 무엇인지를 정의하지만, 어떻게 하는지는 정의하지 않음.<br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 초보자가 이를 기술하면 AI가 나머지를 채워주는 방식.<br>
➜ 예) Bag의 추상 자료형<br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 내용물을 데이터, 일반적인 행동을 연산으로 비유. <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 이후 각 연산에 인터페이스를 달아 사용자 프로그램으로 확장시킬 수 있음.<br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ Bag ADT (Abstract Data Type) <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 데이터 간 중복 허용, 순서 없음, 비교 가능. 리스트. <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 인자(파라미터)의 유뮤는 괄호 안 매개체의 유무로 표시. insert(e), count().<br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ Bag을 클래스로 구현한 후, 메서드를 달자.<br>
</details>



<details><summary>
예시코드 1, 2
</summary>
  
```py

# Bag ADT 설계

class bag :

    def contains(bag, e) :
        if e in bag:
            return True
        else:
            print("bag isn't contain!")

    def insert(bag, e):
        bag.append(e)

    def remove(bag, e):
        bag.remove(e)

    def count(bag):
        if bag:
            return print(len(bag))
        else:
            print("error : bag is false")

    def numOf(bag,e):
        v=0;
        for i in range(len(bag)):
            if e==bag[i]:
                v+=1
        if bag:
            return print(v)
```
  
```py

# Bag ADT 설계

class Bag:

    def __init__(self):
        self.items = []

    def insert(self, e):
        self.items.append(e)

    def remove(self, e):
        self.items.remove(e)

    def contains(self, e):
        return e in self.items

    def count(self):
        return len(self.items)

    def numOf(self, e):
        v=0;
        for i in range(len(bag)):
            if e==bag[i]:
                v+=1
        if bag:
            return print(v)

```

</details>











<details><summary>
알고리즘의 성능 분석
</summary>
➜ 시간 <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 동일한 HW/SW 환경에서 실제로 구현해야 함.<br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ import time에 time.time() 하여 시간차 보기 <br>
➜ 복잡도<br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 시간 복잡도 분석 ; 연산의 횟수를 보고 수행 시간을 분석<br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 공간 복잡도 분석 ; 필요한 메모리 공간 분석<br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 알고리즘 연산 횟수 T(n). 대입 연산자는 다른 연산자와 같이 1번으로, 반복을 제어하는 문은 무시.return도 무시. <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 빅 오 O(n)(최악의 경우) : 계산 쉽고 중요한 의미, 널리 사용됨. 빅 오메가 (최소의 경우), 의미가 없음. 빅 세타 (평균의 경우), 계산하기 상당히 까다로움.<br>
</details>

https://github.com/inha20/DataStructure/issues/1
























