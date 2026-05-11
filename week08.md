# 스택 이어서 

> Depth First Search는 stack을 이용하는 알고리즘

<details>
    <summary>파이썬 코드</summary>

    
```py

from ArrayStack import ArrayStack

map = [
    [1,1,1,1,1,1],
    ['e',0,0,0,0,1],
    [1,0,1,0,1,1],
    [1,1,1,0,0,'x'],
    [1,1,1,0,1,1],
    [1,1,1,1,1,1]
]

MAXSIZE=6

def isValidPos(x,y):
    if 0<=x<MAXSIZE and 0<=y<MAXSIZE:
        if map[y][x]==0 or map[y][x]=='x':
            return True
    return False

def DFS():
    print("DFS: ")
    stack=ArrayStack(100)
    stack.push((0,1))

    while not stack.isEmpty():
        here=stack.pop()
        print(here, end="=>")

        (x,y)=here

        if(map[y][x]=='x'):
            return True
        else:
            map[y][x]="."
            if isValidPos(x,y-1):stack.push((x,y-1))#상
            if isValidPos(x,y+1):stack.push((x,y+1))#하
            if isValidPos(x-1,y):stack.push((x-1,y))#좌
            if isValidPos(x+1,y):stack.push((x+1,y))#우
        print("현재 스택: ", stack)
    return False


result = DFS()
if result: print("미로 탈출 성공!")
else: print("미로 탈출 실패")
print("\n[최종 지도]")
for row in map:
    print(row)



```

</details>




# 큐와 원형큐

> 원형큐는 append O(n)을 O(1)으로 줄이기 위함

<details>
    <summary>파이썬 코드</summary>

    
```py
class CircularQueue:
    def __init__(self, capacity):
        self.capacity=capacity
        self.array=[None]*capacity
        self.front=0
        self.rear=0

    def isEmpty(self):
        return self.front==self.rear
    def isFull(self):
        return self.front==(self.rear+1)%self.capacity
    def enqueue(self, e):
        if not self.isFull():
            self.rear=(self.rear+1)%self.capacity
            self.array[self.rear]=e
    def dequeue(self):
        if not self.isEmpty():
            self.front=(self.front+1)%self.capacity
            return self.array[self.front]
    def peek(self):
        if not self.isEmpty():
            return self.array[(self.front+1)%self.capacity]
    def __str__(self):
        if self.front<self.rear:
            return str(self.array[self.front+1:self.rear+1])
        else:
            return str(self.array[self.front+1:self.capacity]+self.array[0:self.rear+1])
    def totalElementCount(self):
        return (self.rear-self.front+self.capacity)%self.capacity + "개"    
#TestProgram
if __name__=="__main__":
    q=CircularQueue(8)
    q.enqueue('A')
    q.enqueue('B')
    q.enqueue('C')
    q.enqueue('D')
    q.enqueue('E')
    q.enqueue('F')
    print("ABCDEF 삽입 : ",q)
    print("삭제 : ", q.dequeue())
    print("삭제 : ", q.dequeue())
    print("삭제 : ", q.dequeue())
    print("3번 삭제 후 : ",q)
    q.enqueue('G')
    q.enqueue('H')
    q.enqueue('I')
    print("GHI 삽입 : ",q)

```

</details>

> Breath First Search는 queue를 이용하는 알고리즘

<details>
    <summary>파이썬 코드</summary>

    
```py
from CircularQueue import CircularQueue 

map = [
    [1,1,1,1,1,1],
    ['e',0,1,0,0,1],
    [1,0,0,0,1,1],
    [1,0,1,0,1,1],
    [1,0,1,0,0,'x'],
    [1,1,1,1,1,1]
]

MAXSIZE=6

def isValidPos(x,y):
    if 0<=x<MAXSIZE and 0<=y<MAXSIZE:
        if map[y][x]==0 or map[y][x]=='x':
            return True
    return False

def BFS():
    print("BPS: ")
    queue=CircularQueue(100)
    queue.enqueue((0,1))

    while not queue.isEmpty():
        here=queue.dequeue()
        print(here, end="=>")

        (x,y)=here

        if(map[y][x]=='x'):
            return True
        map[y][x]="."
        if isValidPos(x,y-1):queue.enqueue((x,y-1))#상
        if isValidPos(x,y+1):queue.enqueue((x,y+1))#하
        if isValidPos(x-1,y):queue.enqueue((x-1,y))#좌
        if isValidPos(x+1,y):queue.enqueue((x+1,y))#우
        print("현재 큐: ", queue)
    return False


result = BFS()
if result: print("미로 탈출 성공!")
else: print("미로 탈출 실패")
print("\n[최종 지도]")
for row in map:
    print(row)


```
return trun 밑의 코드는 else로 묶어도 되고 안묶어도 알고리즘으로는 같아.

</details>

# 덱

<details>
    <summary>파이썬 코드</summary>

    
```py
from CircularQueue import *

class CircularDeque(CircularQueue):
    def __init__(self, capacity=8):
        super().__init__(capacity)

    def addRear(self,item):
        return super.enqueue(item)

    def deleteFront(self):
        return super.dequeue()
    
    def getFront(self):
        return super.peek()
    
    def addFront(self, item):
        if not self.isFull():
            self.array[self.front]=item
            self.front=(self.front-1+self.capacity)%self.capacity
        else:pass

    def deleteRear(self):
        if not self.isEmpty():
            item=self.array[self.rear]
            self.rear=(self.rear-1+self.capacity)%self.capacity
            return item
        else:pass

    def getRear(self):
        if not self.isEmpty():
            item=self.array[self.rear]
            return item
        else:pass

if __name__=="__main__":
    dq=CircularDeque()
    for i in range(7):
        if i%2==0: dq.addRear(i)
        else: dq.addFront(i)
    print(dq)
    for i in range(2):dq.deleteFront()
    for i in range(3):dq.deleteRear()
    print(dq)
```

</details>


