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
        n=Node(item)
        n.link=self.top
        self.top=n
        #self.top=Node(item, self.top)

    def pop(self):
        if not self.isEmpty():
            n=self.top
            self.top=n.link
            return n.data
        
    def peek(self):
        if not self.isEmpty():
            return self.top.data
        
    def size(self):
        node=self.top
        count=0
        while node != None:
                node=node.link
                count+=1
        return count

    def __str__(self):
        arr=[]
        node=self.top
        while node != None:
            arr.append(node.data)
            node=node.link
        return str(arr)
    
#Test
if __name__=="__main__":
    s=LinkedStack()
    print("연결리스트 스택 : ", s)
    msg=input("문자열 입력: ")
    for c in msg:
        s.push(c)
    print("문자열 연결리스트 스택 : ", s)  
    print("노드의 갯수: ", s.size(), "개") 
    print("문자열 pop 결과:", end='')
    while not s.isEmpty():
        print(s.pop(), end=' ')

    

```

</details>



> LinkedStack
<details>
    <summary>파이썬 코드</summary>

    
```py
class Node:
    def __init__ (self, elem, link=None):
        self.data=elem
        self.link=link
        
class LinkedStack:
    def __init__(self):
        self.top=None
        
    def isEmpty(self):
        return self.top==None
    
    def isFull(self):
        return False
    
    def push(self, item):
        self.top=Node(item, self.top)
    
    def pop(self):
        if not self.isEmpty():
            data=self.top.data
            self.top=self.top.link
            return data
            
    def peek(self):
        if not self.isEmpty():
            return self.top.data
        
    def size(self):
        node=self.top
        count=0
        while not node==None:
            node=node.link
            count+=1
        return count
    
    def __str__(self):
        arr=[]
        node=self.top
        while not node==None:
            arr.append(node.data)
            node=node.link
        return str(arr)
        
if __name__=="__main__":
    s=LinkedStack()
    
    print("스택",s)
    msg=input("문자열 입력 : ")
    for c in msg:
        s.push(c)
        
    print("스택",s)    
            
    print("문자열 출력 : ", end='')
    while not s.isEmpty():
        print(s.pop(), end='')
    print()
    print("스택",s)
            
```

</details>


> LinkedList
<details>
    <summary>파이썬 코드</summary>

    
```py
class Node:
    def __init__ (self, elem, next=None):
        self.data=elem
        self.link=next
        
class LinkedList:
    def __init__(self):
        self.head=None
        
    def isEmpty(self):
        return self.head==None
    
    def isFull(self):
        return False

    def getNode(self, pos):
        if pos<0: return None
        node=self.head
        while pos>0 and node!= None:
            node=node.link
            pos -=1
        return node
    
    def getEntry(self, pos):
        node=self.getNode(pos)
        if node == None : return None
        else : return node.data
        
    def insert(self, pos, elem):
        before = self.getNode(pos-1)
        if before == None:
            self.head = Node(elem, self.head)
        else:
            node = Node(elem, before.link)
            before.link=node
            
    def delete(self, pos):
        before = self.getNode(pos-1)
        if before == None:
            if self.head is not None:
                self.head = self.head.link
        elif before.link != None:
            before.link=before.link.link
            
    def size(self):
        node=self.head
        count=0
        while node is not None:
            node=node.link
            count+=1
        return count
    
    def __str__(self):
        arr=[]
        node=self.head
        while not node==None:
            arr.append(node.data)
            node=node.link
        return str(arr)
    
    def replace(self, pos, elem):
        node = self.getNode(pos)
        if node != None :
            node.data = elem
            
    def find(self, val):
        node = self.head
        while node is not None:
            if node.data == val:
                return node
            node=node.link
        return node
    
if __name__=="__main__":
    L=LinkedList()
    L.insert(0,10)
    L.insert(0,20) 
    L.insert(1,30)
    L.insert(3,40)
    L.insert(2,50)  
    L.delete(2)
    print(L)
    L.delete(3)
    print(L)
    L.delete(0)
    print(L)

            
```

</details>

