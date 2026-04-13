# 리스트 : 선형 자료구조


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
    <summary> 파이썬 코드   </summary>
    
```python
class ArraySet:
    def __init__(self, capacity=100):
        self.capacity=capacity
        self.size=0
        self.array=[None]*capacity

    def isEmpty(self):
        return self.size==0

    def isFull(self):
        return self.size==self.capacity
    
    def __str__(self):
        return str(self.array[0:self.size])

    def contains(self,e):
        for i in range(self.size):
            if self.array[i]==e:
                return True
        return False
    
    def insert(self,e):
        if not self.contains(e) and not self.isFull():
            self.array[self.size]=e
            self.size+=1
        else : pass

    def delete(self,e):
        for i in range(self.size):
            if self.array[i]==e:
                self.array[i]=self.array[self.size-1]
                self.size -=1

    def union(self, setB):
        setC=ArraySet()
        for i in range(self.size):
            setC.insert(self.array[i])
        for i in range(setB.size):
            if not setC.contains(setB.array[i]):
                setC.insert(setB.array[i])
        return setC
    
    def intersection(self, setB):
        setC=ArraySet()
        for i in range(self.size):
            if setB.contains(self.array[i]):
               setC.insert(self.array[i])
        return setC
    
    def difference(self, setB):
        setC=ArraySet()
        for i in range(self.size):
            if not setB.contains(self.array[i]):
               setC.insert(setB.array[i])
        return setC
    
    def __eq__(self, setB):
        if self.size != setB.size:
            return False
        for i in range(self.size):
            if not setB.contains(self.array[i]):
                return False
        return True
    
    def isSubsetOf(self, setB): 
        for i in range(self.size):
            if not setB.contains(self.array[i]):
                return False
        return True
```
</details>






