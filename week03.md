# 리스트 : 선형 자료구조

> 0을 뒤로 옮기기

<details>
    <summary>리스트 개론</summary>
➜ 항목들은 순서와 위치를 가짐. <br>
➜ 임의의 위치에서 삽입, 삭제 가능.<br>
➜ 연산에 대한 인자의 갯수는 0개 이상.<br>
➜ 배열 구조 : 삽입, 삭제시 크기 변경. vs 연결 구조 : 구현이 복잡하고 항목 접근이 O(n)으로 느림.<br>
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
```py
from ArrayList import ArrayList

List=ArrayList(1000)

while True:
    command=input("[메뉴선택] i-입력, d-삭제, r-변경, p-출력, l- 파일읽기, s-저장, q-종료");
    
    if command=="i":
        pos = int(input("입력 행 번호 0번부터 : "))
        str = input("내용 : ")
        List.insert(pos,str)
    elif command=="d":
        pos = int(input("삭제 행 번호 0번부터 : "))
        List.delete(pos)
    elif command=="r":
        pos = int(input("변경 행 번호 0번부터 : "))
        str = input("내용 : ")
        List.replace(pos,str)
    elif command=="p":
        print("Line Editor")
        for line in range(List.size):
            print("[%2d] "%line, end="")
            print(List.getEntry(line))
        print()
    elif command=="q":
        exit()
    elif command=="l":
        filename="test.txt"
        infile=open(filename, "r", encoding="utf-8")
        lines=infile.readlines()
        for line in lines:
            List.insert(List.size,line.rstrip("\n"))
        infile.close()
    elif command=="s":
        filename="test.txt"
        outfile=open(filename, "w", encoding="utf-8")
        len=List.size
        for i in range(len):
            outfile.write(List.getEntry(i)+"\n")
        outfile.close()

```

    
</details>

# 집합 : 비선형 자료구조


<details>
    <summary>투 포인터 활용</summary>
    
```python
ExampleInputList = [0, 1, 0, 2, 3, 0, 0]
IndexZero = 0
for Index, Value in enumerate(ExampleInputList):
    if Value != 0:
        ExampleInputList[IndexZero] = Value
        if IndexZero != Index:
            ExampleInputList[Index] = 0
        IndexZero += 1
print(ExampleInputList)
```
선형시간과 상수공간을 만족시킨다는 점에서 기존보다 개선된 알고리즘이다. <br>
Value가 0일 때 작동되는 코드 없이, 0이지 않을 때만 위와 같은 코드가 작동한다. 그럼에도 불구하고 0이 뒤쪽으로 옮겨지는 것은 어떻게 한 것일까? temp=a; a=b; b=temp를 메서드로 쓰기라도 했단 말인가? 이를 사용하는 매우 비효율적인 코드 대신에, 더 간단한 0이 뒤로 밀려나는 방법을 사용하였다. Value가 0이지 않을 경우에만 리스트 앞쪽으로 값을 가져오고(if Value != 0: ; ExampleInputList[IndexZero] = Value), 이후 기존 자리에 0을 대입 연산하는 조건으로 (if IndexZero != Index: )를 배치시킨 후 그 다음 숫자를 받을 준비를 위해 (IndexZero += 1)를 둔 것이다. 들여쓰기를 적절히 조절하는 것도 잊지 말자.
</details>






