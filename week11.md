# 연결리스트
> 큐로 스택 만들기
<details>
    <summary>파이썬 코드</summary>

    
```py
#단방향 노드
class Node:
    def __init__(self, e, link=None):
        self.data = e
        self.link=link

# 단순 연결 스택 글래스   
class LinkedStack:
    def __init__(self):
        self.top=None

    def isEmpty(self):
        return self.top==None
    
    def isFull(self):
        return False
    
    def push(self,item):
        self.top=Node(item, self.top)

    def pop(self):
        if not self.isEmpty():
            n=self.top
            self.top=n.link
            return n.data
        
    def peek(self):
        if not self.isEmpty():
            return self.top.data
```

</details>
