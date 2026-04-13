# 스택

<details>
    <summary>스택 개론</summary>
➜ top, elements, LIFO <br>
➜ top이 달라지면 구조가 바뀐다고 표현함.<br>
➜ 예시 <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 입 출력을 역순으로.  <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ undo(되돌리기).  <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 이전폐이지로 이동.  <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 함수 호출(시스템 스택). <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 괄호 검사. <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 미로 탐색. <br>
</details>

<details>
    <summary>파이썬 코드</summary>
그림에서의 화살표를 기준으로 등호와 부등호, -1, +1에 주의하자. <br>
리턴값을 출력할 땐 print문 안에 넣자.
    
```py

#데이터멤버_전역변수선언
capacity=100
size=0
array=[None]*capacity

#isEmpty 선언
def isEmpty():
    if size==0 :
        return True
    else : 
        return False

#isFull 선언
def isFull():
    if size==capacity :
        return True
    else :
        return False

#getEntry 선언
def getEntry(pos):
    if 0<=pos<size:
        return array[pos]
    else:
        return None
 
#insert 선언
def getEntry(pos,e):
    global size
    if 0<=pos<size and not isFull():
        for i in range(size, pos,-1):
            array[i]=array[i-1] 
        array[pos]=e
        size+=1
        return array[pos]
    else:
        print("리스트가 오버플로우 또는 유효하지 않은 삽입 위치")
        exit()


#delete 선언
def delete(pos):
    global size
    if 0<=pos<size and not isEmpty():
        R=array[pos]
        for i in range(pos, size-1):
            array[i]=array[i+1] 
        size-=1
        return R
    else:
        print("리스트가 언더플로우 또는 유효하지 않은 삽입 위치")
        exit()
```
```py
class ArrayList:
    def __init__(self, capacity=100)
        self.capacity=capacity
        self.size=0
        self.array=[None]*capacity

    def isEmpty(self):
        return self.size==0

    def isFull(self):
        return size==self.capacity

    def getEntry(self,pos):
        if 0<= pos <self.size:
            return self.array[pos]
        else :
            return None
 
    def insert(self, pos,e):
        if 0<= pos <=self.size and not self.isFull():
            for i in range(self.size, pos,-1):
                self.array[i]=self.array[i-1] 
            self.array[pos]=e
            size+=1
            return self.array[pos]
        else:pass

    def delete(self, pos):
        global size
        if 0<= pos <size and not self.isEmpty():
            R=self.array[pos]
            for i in range(pos, size-1):
                self.array[i]=self.array[i+1] 
            size-=1
            return R
        else:pass

    def __str__(self):
        return str(self.array[0:self.size])
    
    def replace(self, pos,e):
        if 0<= pos <=self.size:
            self.array[pos]=e

    def count(self, e):
        TotalCount=0
        for i in range(0,self.size):
            if self.array[i] == e:
                TotalCount += 1
        return print(TotalCount)

```
